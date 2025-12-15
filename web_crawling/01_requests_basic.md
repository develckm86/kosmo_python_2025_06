# 1. requests로 기본 조회하기

## 준비
- 가상환경 활성화: `source venv/bin/activate`
- 라이브러리 설치:
  ```bash
  pip install requests beautifulsoup4
  ```

## 단순 GET 요청
```python
import requests

url = "https://example.com"
resp = requests.get(url, timeout=5)
resp.raise_for_status()  # 200이 아닐 때 예외

print(resp.status_code)
print(resp.headers.get("Content-Type"))
print(resp.text[:200])  # HTML 앞부분만 확인
```

## HTML 파싱 (BeautifulSoup)
```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(resp.text, "html.parser")
title = soup.find("title").get_text(strip=True)
links = [a["href"] for a in soup.select("a[href]")]

print("title:", title)
print("link count:", len(links))
```

## 기본 흐름 정리
- `requests.get` → `raise_for_status` → `resp.text` 확인 → `BeautifulSoup` 파싱 → 필요한 요소 추출.

## 체크 포인트
- `timeout`은 항상 지정.
- `resp.encoding`이 이상하면 `resp.encoding = "utf-8"`처럼 강제 설정 가능.
