_created: 2025-12-11 (updated: 2025-12-14)_

# 파이썬 숫자(number) 자료형 정리

## 1. 숫자 타입 개요
- 모두 객체로 동작하며 기본형/참조형 구분이 없다.
- 주요 타입: `int`(정수, 크기 제한 없음), `float`(부동소수, IEEE 754), `complex`(복소수, `a + bj`).

## 2. 정수(int)
```python
i = 10
print(i, type(i))

i, j = 10, 3
print(i / j)   # 나눗셈 → float
print(i // j)  # 몫
print(i % j)   # 나머지
print(i ** j)  # 거듭제곱

i = 10_000_000  # 가독성용 언더스코어
print(i, type(i))
```
- 메모리가 허용하는 한 크기 제한이 없다.

## 3. 실수(float)
```python
i = 3.14
print(i, type(i))

i = 3.14e3  # 3.14 × 10³
print(i)

i = 3e3     # 3000.0
print(i)
```
- 2진 부동소수이므로 10진 소수를 정확히 표현하지 못할 수 있다.

## 4. 부동소수 오차
```python
print(0.1 + 0.2)          # 0.30000000000000004
print(0.1 + 0.2 == 0.3)   # False
```
- 2진수 분모가 2의 거듭제곱일 때만 정확히 표현된다(예: 0.5=1/2, 0.25=1/4).
- 0.1처럼 10진수를 2진으로 딱 맞게 표현 못하면 근사값이 된다.

## 5. 복소수(complex)
```python
z = 3 + 2j
print(z, type(z))

z1, z2 = 3 + 2j, 1 - 4j
print(z1 + z2)  # (4-2j)
print(z1 * z2)  # (11-10j)
```
- 허수 단위는 `j`를 사용한다.

## 6. 연산자 요약
- 산술: `+ - * / // % **`
- 비교: `== != > >= < <=`
- 논리: `and or not` (단락 평가)
- 멤버십: `in`, `not in`
- 동일성: `is`, `is not` (`None` 체크에 주로 사용)
- 비트: `& | ^ ~ << >>` (정수용)
- 할당/복합 할당: `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=` 등
- 우선순위 참고: `**` > 단항 부호 > `* / // %` > `+ -` > 비교 > `not` > `and` > `or`

## 7. 산술·비교·부호 예시
```python
a, b, c = 10, 20, -30

print(a + b, a - b, a * b)
print(a / b, a // b, a % b, a ** b)

print(a == b, a != b, a > b, a < b, a >= b, a <= b)
print(a is b, a is not b)
print(-a, +a)
```
- `is`는 객체 동일성 비교이므로 값 비교에는 쓰지 않는다.

## 8. 유용한 내장 수학 함수
```python
print(abs(c))        # 절댓값
print(pow(a, 3))     # 거듭제곱
print(divmod(a, 3))  # (몫, 나머지)

print(round(2.5))    # 2 (은행가 반올림: 짝수 쪽)
print(round(3.5))    # 4

print(bin(10), oct(10), hex(10))  # 2/8/16진수 문자열
```

## 9. math 모듈 예시
```python
import math

print(math.sqrt(16))   # 제곱근
print(math.ceil(3.2))  # 올림
print(math.floor(3.8)) # 내림
print(math.trunc(3.9)) # 버림(소수점 제거)
```
