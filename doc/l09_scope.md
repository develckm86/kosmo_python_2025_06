_created: 2025-12-11 (update 날짜 적어주세요)_

# 1. 스코프 기본 개념
- 이름(변수/함수/클래스)이 유효한 범위. 파이썬은 LEGB 순서로 찾는다: Local → Enclosed → Global → Builtins.
- `{}` 블록 스코프가 없다. `if/for/while` 안에서 만든 이름도 같은 함수/모듈 스코프에 남는다.

# 2. 전역과 지역 나누기
- **전역(Global)**: 모듈 최상단 이름. 어디서나 읽을 수 있지만 수정 시는 주의.
- **지역(Local)**: 함수 내부에서 대입된 이름. 함수 실행 중에만 존재.
- **중첩 함수(Enclosed)**: 바깥 함수의 지역을 안쪽 함수가 참조할 때 해당 영역이 Enclosed가 된다.
- 전역 수정: `global x` 선언 후 대입. 남용보다 반환값으로 갱신하는 쪽이 안전.
- 바깥 지역 수정: `nonlocal x` 선언 후 대입. 중첩 함수에서만 사용.

# 3. 들여쓰기(탭/스페이스)와 블록
- 파이썬은 들여쓰기로 블록을 구분하지만, 블록이 스코프를 만들지 않는다(함수·클래스·컴프리헨션 정도만 새 스코프).
- 탭/스페이스 혼용 금지(PEP 8: 스페이스 4칸). 들여쓰기 오류는 스코프 문제라기보다 문법 오류로 바로 드러난다.

# 4. builtins 모듈
- 파이썬이 시작될 때 자동으로 로드되는 **최상위 네임스페이스**. `import builtins`로 볼 수 있다.
- 주요 내장 함수(간략 설명):  
  - `print`: 출력  
  - `len`: 길이(시퀀스/컬렉션)  
  - `sum`: 합계(`sum(iterable)`; 두 수 더하기는 `a + b`)  
  - `min`/`max`: 최소/최대  
  - `range`: 숫자 시퀀스 생성  
  - `enumerate`: 인덱스와 값 묶기  
  - `zip`: 여러 시퀀스 병렬 묶기  
  - `map`/`filter`: 함수 적용/필터링  
  - `any`/`all`: 하나라도 참/모두 참  
  - `sorted`/`reversed`: 정렬/역순  
  - `input`: 문자열 입력  
  - `open`: 파일 열기  
  - `abs`/`round`/`pow`: 절댓값/반올림/거듭제곱  
  - `dir`: 속성/이름 목록 확인
- 주요 내장 타입/예외: `int`, `float`, `str`, `bool`, `list`, `dict`, `set`, `tuple`, `bytes`, `bytearray`, `frozenset`, `complex`, `object`, `type`, `Exception`, `ValueError`, `TypeError`, `KeyError` 등.
- 확인 방법: `import builtins; print(dir(builtins))`로 목록 확인. 덮어쓰면 해당 기능을 잃으므로 변수명 충돌에 특히 주의.


# 5. 이름 충돌과 예시
- 내장/표준 이름 덮어쓰기 금지: `list`, `dict`, `str`, `sum` 등은 `builtins`에 있다.
  ```python
  sum = 10              # builtins.sum 덮어씀
  nums = [1, 2, 3]
  # print(sum(nums))    # TypeError 발생
  del sum               # 복구
  print(sum(nums))      # 6
  ```
- 전역/지역 이름이 같으면 지역이 우선: 전역 값은 유지되므로 의도에 맞게 이름을 다르게 잡기.

# 6. 내부/외부 라이브러리 네임스페이스
- 내부(표준) 라이브러리: `import math` 후 `math.pi`처럼 모듈 이름을 접두사로 사용.
- 외부(서드파티) 라이브러리: 설치 후 동일하게 `import requests` → `requests.get`.
- `from module import name`는 이름을 현재 스코프로 올려 충돌 가능성이 높다. 필요 시 `import module as alias`로 네임스페이스를 유지.


# 7. 기억할 것
- 블록 스코프 없음: 제어문 안에서 만든 이름이 밖으로 새어 나오는지 항상 의식.
- 전역 상태 변경 최소화, 필요 시 명시적 선언 사용.
- 라이브러리 임포트 시 네임스페이스를 유지해 충돌을 피하기.
