_created: 2025-12-11 (updated: 2025-12-14)_

# 파이썬 조건문(if)

## 1. 기본 형태: if / else
```python
age = 20

if age >= 18:
    status = "성인"
else:
    status = "미성년자"

print(status)
```
- 조건이 참인 블록만 실행되며, 들여쓰기로 블록을 구분한다.

## 2. 조건부 표현식(삼항 연산자)
```python
age = 17
status = "성인" if age >= 18 else "미성년자"
print(status)
```
- 짧게 값을 고를 때 사용한다. 로직이 길어지면 일반 `if` 블록이 더 읽기 쉽다.

## 3. 다중 분기: if / elif / else
```python
score = 85

if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'
elif score >= 70:
    grade = 'C'
elif score >= 60:
    grade = 'D'
else:
    grade = 'F'

print(grade)
```
- 위에서부터 순서대로 평가하며 처음 참인 분기만 실행된다.

## 4. 조건부 표현식으로 다중 분기하기
```python
score = 75
grade = ('A' if score >= 90 else
         'B' if score >= 80 else
         'C' if score >= 70 else
         'D' if score >= 60 else
         'F')

print(grade)
```
- 한 줄에 모두 적을 수 있지만, 줄바꿈과 들여쓰기로 가독성을 유지한다.

## 5. Python 3.10+: match 문법
```python
score = 75
match score:
    case s if s >= 90:
        grade = 'A'
    case s if s >= 80:
        grade = 'B'
    case s if s >= 70:
        grade = 'C'
    case s if s >= 60:
        grade = 'D'
    case _:
        grade = 'F'
print(grade)
```
- 패턴 매칭으로 조건을 나열할 수 있다. 가드(`if`)를 함께 써서 범위를 표현한다.

## 6. 연습 거리
- 나이 입력 후 성인/미성년자 메시지 출력하기.
- 점수 입력 후 등급 출력하기(조건부 표현식과 `match` 둘 다 시도).
- 여러 조건을 섞어 통과/탈락 여부 판단하기(`and`, `or` 활용).
