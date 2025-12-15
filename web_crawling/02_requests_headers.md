# 2. requests로 헤더/세션 제어하기

## 준비
- `pip install requests beautifulsoup4` (이미 설치했다면 생략)

## User-Agent, Referer 지정
```python
import requests

url = "https://example.com"
headers = {
    "User-Agent": "Mozilla/5.0 (compatible; crawl-practice/1.0)",
    "Referer": "https://google.com",
}

resp = requests.get(url, headers=headers, timeout=5)
resp.raise_for_status()
```

## 세션(Session)으로 쿠키/연결 재사용
```python
from bs4 import BeautifulSoup

session = requests.Session()
session.headers.update({"User-Agent": "Mozilla/5.0"})

# 1) 첫 요청: 쿠키 발급
resp1 = session.get("https://httpbin.org/cookies/set?token=abc", timeout=5)
resp1.raise_for_status()

# 2) 두 번째 요청: 같은 세션으로 쿠키 전달
resp2 = session.get("https://httpbin.org/cookies", timeout=5)
resp2.raise_for_status()

print(resp2.json())  # {"cookies": {"token": "abc"}}
```

## 폼 데이터 POST 예시
```python
login_url = "https://httpbin.org/post"
data = {"id": "user", "pw": "pass"}

r = session.post(login_url, data=data, timeout=5)
r.raise_for_status()
print(r.json())  # form 키 안에 전송된 값 확인
```

## 체크 포인트
- 헤더로 간단한 차단 우회 시도(User-Agent, Referer).
- 세션으로 쿠키 유지, Keep-Alive 재사용.
- 서버 정책을 존중: 너무 잦은 요청은 `time.sleep`으로 간격 주기.
