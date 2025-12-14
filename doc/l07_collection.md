_created: 2025-12-11 (update 날짜 적어주세요)_

# 파이썬 컬렉션 자료형 정리
입문자용으로 컬렉션 개념 → 핵심 포인트 → 코드 예시 순서로 정리했습니다.

## 1. 컬렉션 개요
- 여러 데이터를 한 변수에 묶어 관리하는 자료형. 반복문과 함께 자주 사용.
- 대표 타입: `list`, `tuple`, `dict`, `set`.

## 2. 리스트(list)
- 특징: 순서 보장, 중복 허용, 값 변경 가능(mutable).
- 생성
  ```python
  numbers = [10, 20, 30]
  names = ["kim", "lee", "park"]
  mixed = [1, "a", 3.14, True]
  empty = []
  ```
- 인덱스/슬라이싱 (`start:stop:step`, stop은 제외)
  ```python
  numbers[0], numbers[-1]
  numbers[1:3], numbers[-2:]
  numbers[::2], numbers[::-1]
  ```
- 수정
  ```python
  numbers[1] = 99
  ```
- 주요 메서드
  ```python
  numbers.append(40)
  numbers.insert(1, 15)
  numbers.remove(20)
  numbers.pop()     # 맨 뒤 삭제 후 반환
  len(numbers)
  ```

## 3. 튜플(tuple)
- 특징: 리스트와 유사하지만 불변(immutable). 읽기 전용 데이터에 적합.
- 생성
  ```python
  point = (10, 20)
  colors = ("red", "green", "blue")
  single = (10,)  # 콤마 필수
  ```
- 수정 불가 예
  ```python
  # point[0] = 5  # 오류
  ```
- 주 사용처: 좌표, 설정 값, 변경되면 안 되는 데이터.

## 4. 딕셔너리(dict)
- 특징: `key: value` 쌍 저장, 키 중복 불가, 입력 순서 유지(3.7+).
- 생성/접근/수정
  ```python
  student = {"name": "kim", "age": 20, "score": 90}
  student["age"] = 21
  student["major"] = "computer"
  print(student["name"])
  del student["score"]
  ```
- 주요 메서드
  ```python
  student.keys()
  student.values()
  student.items()
  student.get("phone")  # 없으면 None
  ```

## 5. 집합(set)
- 특징: 중복 없음, 순서 없음, 집합 연산 제공.
- 생성/중복 제거
  ```python
  nums = {1, 2, 3, 3}
  unique = set([1, 1, 2, 3])
  ```
- 연산
  ```python
  a, b = {1, 2, 3}, {3, 4, 5}
  a | b  # 합집합
  a & b  # 교집합
  a - b  # 차집합
  ```

## 6. 공통 활용
```python
for n in numbers:
    print(n)

for key, value in student.items():
    print(key, value)

10 in numbers        # 멤버십 검사
"name" in student
```

## 7. 선택 기준
- `list`: 순서 필요, 값 변경 필요, 가장 일반적.
- `tuple`: 변경 불가 데이터, 안전성 강조.
- `dict`: 의미 있는 데이터 묶음, 키 기반 접근.
- `set`: 중복 제거, 집합 연산 필요.

## 8. 실습 아이디어
- 리스트로 점수 관리, 평균/최대 구하기.
- 튜플 좌표 두 점 거리 계산.
- 딕셔너리로 회원 정보 CRUD 실습.
- `set`으로 중복 제거 후 합집합/교집합 확인.
