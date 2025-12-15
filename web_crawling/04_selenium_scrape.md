# 4. Selenium으로 데이터 가져오기 (대기/스크롤)

## 준비
- `pip install selenium`
- `chromedriver` 준비 (PATH 또는 절대 경로 지정).

## 명시적 대기(Explicit Wait)
```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

options = Options()
options.add_argument("--headless")
driver = webdriver.Chrome(options=options)

driver.get("https://example.com")

wait = WebDriverWait(driver, 10)
title_el = wait.until(EC.visibility_of_element_located((By.TAG_NAME, "h1")))
print(title_el.text)

driver.quit()
```

## 스크롤 다운 후 데이터 추출
```python
from selenium.webdriver.common.keys import Keys
import time

driver = webdriver.Chrome(options=options)
driver.get("https://example.com")

body = driver.find_element(By.TAG_NAME, "body")
for _ in range(3):  # 세 번 스크롤
    body.send_keys(Keys.END)
    time.sleep(1)  # 로딩 대기

links = [a.get_attribute("href") for a in driver.find_elements(By.CSS_SELECTOR, "a")]
print("links:", len(links))

driver.quit()
```

## 페이지 내에서 데이터 추출
```python
items = driver.find_elements(By.CSS_SELECTOR, ".item")
for item in items:
    title = item.find_element(By.CSS_SELECTOR, ".title").text
    price = item.find_element(By.CSS_SELECTOR, ".price").text
    print(title, price)
```

## 체크 포인트
- 동적 로딩 → `WebDriverWait` + `expected_conditions`.
- 무한 스크롤 → 키 입력 혹은 `execute_script("window.scrollTo(...)")` 활용.
- 헤드리스/헤드 모드는 옵션으로 전환.
- 크롤링 예절: 요청 간격 두기, 서비스 약관/robots.txt 확인.
