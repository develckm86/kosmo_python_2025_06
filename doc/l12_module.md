# 파이썬 모듈(Module) 정리

## 1. 모듈이란?
- 함수, 변수, 클래스들을 모아놓은 **파이썬 파일 1개**가 곧 모듈.
- 코드 재사용과 구조화를 위한 기본 단위.
- 예: `math.py`, `random.py`, `datetime.py`, `myutil.py`(직접 작성)

## 2. import 기본 형태
- 모듈 전체를 불러오며 `모듈명.이름`으로 사용.
```python
import math

math.sqrt(16)
math.pi
```

## 3. from import 방식
- 자주 쓰는 것만 선택해 들여온다. 이름 충돌 가능성은 증가.
```python
from math import sqrt, pi

sqrt(16)
pi
```

## 4. 별칭(alias) 사용
- 이름이 길거나 관례가 있을 때 alias로 짧게 사용.
```python
import numpy as np
import pandas as pd

np.array([1, 2, 3])

from math import sqrt as s
s(25)
```

## 5. 와일드카드 import (비권장)
- `from math import *`처럼 쓰면 **무슨 이름이 들어왔는지 알기 어렵고 충돌 위험**이 크다.
- 수업에서는 "쓰지 말자"고 단호하게 말해도 된다.

## 6. 내가 만든 모듈 사용하기
동일 디렉터리에 파일을 만든 후 import.
```python
# myutil.py
def add(a, b):
    return a + b
```
```python
# main.py
import myutil

print(myutil.add(3, 4))

# 또는
from myutil import add
print(add(3, 4))
```

## 7. 모듈 실행 vs import 구분
- 모듈은 직접 실행도 되고, import도 된다.
- `__name__ == "__main__"` 조건으로 실행 시점만 분리.
```python
# myutil.py
def add(a, b):
    return a + b

if __name__ == "__main__":
    print(add(1, 2))  # 직접 실행할 때만 동작
```
- 테스트 코드/데모 코드를 보호하는 관례.

## 8. 표준 라이브러리 예시
- `math`: 수학 함수
- `random`: 난수
- `datetime`: 날짜/시간
- `os`: 운영체제 기능
- `sys`: 파이썬 인터프리터 정보
```python
import random
print(random.randint(1, 10))
```

## 9. 모듈 검색 순서 (중요)
1. 현재 실행 중인 파일 위치
2. `PYTHONPATH` 경로
3. 표준 라이브러리
4. `site-packages`(pip 설치 패키지)

→ 표준 모듈 이름과 같은 파일명(예: `math.py`)을 피해야 충돌이 없다.

## 10. 패키지(package) 개념
- 모듈 여러 개를 폴더로 묶은 것.
- 폴더 안에 `__init__.py`를 두면 패키지로 인식(요즘은 없어도 동작하지만 두는 편이 명시적).
```
utils/
  __init__.py
  mathutil.py
  strutil.py
```
```python
from utils.mathutil import add
```

## 11. pip와 외부 모듈
- 외부 라이브러리 설치: `pip install requests`
- `pip`은 **모듈 설치 도구**라는 점만 기억.
```python
import requests
```

## 12. 패키지·환경 관리 도구
- **pip**: 기본 패키지 관리자. `pip install requests`
- **venv**: 표준 가상환경. 프로젝트별 격리.
```bash
# 가상환경 생성
python -m venv venv

# 가상환경 활성화 (Windows는 venv\Scripts\activate)
source venv/bin/activate

# 설치된 모듈 확인
pip list

# 모듈 설치
pip install pandas

# 모듈 명세서 생성
pip freeze > requirements.txt

# 명세서 기반 설치
pip install -r requirements.txt

# 가상환경 종료
deactivate
```

## 13. 수업 핵심 요약
- 모듈 = 파이썬 파일 하나.
- import 형태: `import 모듈`, `from 모듈 import 이름`, alias 사용.
- `__name__ == "__main__"`은 데모/테스트 보호용 필수 패턴.
- 표준 모듈 이름과 파일명 충돌 주의.
