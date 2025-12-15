
파이썬 모듈(Module) 사용 방법 정리

1. 모듈이란?
	•	함수, 변수, 클래스들을 모아놓은 파일
	•	파일 하나가 곧 하나의 모듈
	•	코드 재사용과 구조화를 위한 기본 단위

예
	•	math.py
	•	random.py
	•	datetime.py
	•	내가 만든 myutil.py

⸻

2. import 기본 형태

가장 기본적인 사용법

import math

math.sqrt(16)
math.pi

특징
	•	모듈 전체를 가져옴
	•	항상 모듈명.이름 형태로 사용

⸻

3. from import 방식

자주 쓰는 요소만 가져오기

from math import sqrt, pi

sqrt(16)
pi

특징
	•	모듈명 없이 바로 사용 가능
	•	많이 쓰면 이름 충돌 위험

⸻

4. 별칭(alias) 사용

모듈 이름이 길 때

import numpy as np
import pandas as pd

np.array([1, 2, 3])

또는

from math import sqrt as s

s(25)

⸻

5. 모듈 전체 가져오기 (비권장)

from math import *

사용 가능하지만
	•	어떤 이름이 들어왔는지 알기 어려움
	•	이름 충돌 위험 큼

수업에서는

“쓰지 말자”라고 명확히 말해도 됨

⸻

6. 내가 만든 모듈 사용하기

같은 디렉터리에 파일 생성

myutil.py

def add(a, b):
return a + b

main.py

import myutil

print(myutil.add(3, 4))

또는

from myutil import add
print(add(3, 4))

⸻

7. 모듈 실행 vs import 차이

모듈은
	•	실행할 수도 있고
	•	import할 수도 있음

이를 구분하는 문법

if name == “main”:

예

myutil.py

def add(a, b):
return a + b

if name == “main”:
print(add(1, 2))

의미
	•	직접 실행할 때만 아래 코드 실행
	•	import될 때는 실행 안 됨

테스트 코드 보호용

⸻

8. 표준 라이브러리 모듈 예시

자주 쓰는 표준 모듈
	•	math : 수학 함수
	•	random : 난수
	•	datetime : 날짜/시간
	•	os : 운영체제 기능
	•	sys : 파이썬 인터프리터 정보

예

import random
print(random.randint(1, 10))

⸻

9. 모듈 검색 순서 (중요 개념)

파이썬은 import 시 아래 순서로 찾음
	1.	현재 실행 중인 파일 위치
	2.	PYTHONPATH 경로
	3.	표준 라이브러리
	4.	site-packages (pip 설치 패키지)

그래서
	•	파일 이름을 math.py 로 만들면 ❌
	•	표준 모듈 이름과 충돌 주의

⸻

10. 패키지(package) 개념 (한 단계 위)
	•	모듈 여러 개를 폴더로 묶은 것
	•	폴더 안에 init.py (요즘은 없어도 됨)

구조 예

utils/
mathutil.py
strutil.py

사용

from utils.mathutil import add

⸻

11. pip와 외부 모듈

외부 라이브러리 설치 (enve 사용 권장)

pip install requests


사용

import requests

수업 포인트

pip은 “모듈 설치 도구”

⸻

12. 수업 핵심 요약
	•	모듈 = 파이썬 파일
	•	import 방식은 3가지
	•	import 모듈
	•	from 모듈 import 이름
	•	alias 사용
	•	name == “main” 은 필수 개념
	•	표준 모듈 이름과 파일명 충돌 주의

⸻
## 3. 패키지·환경 관리 도구
- **pip**: 기본 패키지 관리자. `pip install requests`
- **venv**: 표준 가상환경. 프로젝트별 격리.
  ```bash
  #가상환경 생성
  python -m venv venv
  #가상환경 선택
  # Windows는 venv\Scripts\activate
  # Windows 오류시 powershell->Set-ExecutionPolicy RemoteSigned->Y

  source venv/bin/activate        
  #설치된 모듈 확인 (pip list)
  pip freeze
  #모듈 설치
  pip install pandas
  
  #모듈 명세서 생성
  pip freeze > requirements.txt
  
  #모듈 명세서 기반 설치 
  pip install -r requirements.txt
  
  deactivate #가상환경 벗어나기
   ```