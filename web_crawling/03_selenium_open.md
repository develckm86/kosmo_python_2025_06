# 3. Selenium으로 브라우저 열기/이동

## 준비
- 가상환경: `source venv/bin/activate`
- 설치:
  ```bash
  pip install selenium
  ```
- 크롬 드라이버 준비: `chromedriver`가 PATH에 있거나, 크롬 버전에 맞게 설치.

## 브라우저 열고 페이지 이동
```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

options = Options()
# options.add_argument("--headless")  # 화면 없이 실행하려면 주석 해제

driver = webdriver.Chrome(options=options)
driver.get("https://example.com")

print(driver.title)
driver.quit()
```

## 요소 찾기 기본
```python
from selenium.webdriver.common.by import By

driver = webdriver.Chrome(options=options)
driver.get("https://example.com")

title_el = driver.find_element(By.TAG_NAME, "h1")
print(title_el.text)

link_els = driver.find_elements(By.CSS_SELECTOR, "a")
print("link count:", len(link_els))

driver.quit()
```

## 체크 포인트
- 드라이버 경로/버전이 맞는지 확인.
- headless 모드는 옵션을 주석 해제.
- `find_element`는 하나, `find_elements`는 여러 개 반환.
