# 파이썬 함수(Function) 수업 정리

## 1. 함수란 무엇인가
- 함수는 **자주 사용하는 코드를 하나의 이름으로 묶은 것**
- 코드 재사용성 증가
- 가독성 향상
- 유지보수 용이

```python
def hello():
    print("Hello Python")


⸻

2. 함수 기본 구조

def 함수이름(매개변수):
    실행문
    return 반환값

	•	def : 함수 정의 키워드
	•	매개변수(parameter) : 입력값
	•	return : 결과 반환 (없으면 None 반환)

⸻

3. 매개변수와 인자

def add(a, b):
    return a + b

result = add(10, 20)
print(result)

	•	매개변수: 함수 정의 시 사용하는 변수
	•	인자: 함수 호출 시 전달하는 값

⸻

4. 반환값(return)

def square(x):
    return x * x

	•	return을 만나면 함수 즉시 종료
	•	return이 없으면 None 반환

def test():
    print("hello")

print(test())  # None


⸻

5. 여러 값 반환
	•	실제로는 튜플 반환

def calc(a, b):
    return a + b, a - b

x, y = calc(10, 3)
print(x, y)


⸻

6. 기본값 매개변수

def greet(name="Guest"):
    print(f"Hello {name}")

greet()
greet("Kim")

	•	호출 시 값을 전달하지 않으면 기본값 사용

⸻

7. 키워드 인자

def info(name, age):
    print(name, age)

info(age=20, name="Kim")

	•	순서 상관없이 전달 가능
	•	가독성 향상

⸻

8. 가변 인자

8-1. *args (튜플)

def add_all(*nums):
    total = 0
    for n in nums:
        total += n
    return total

print(add_all(1, 2, 3, 4))


⸻

8-2. **kwargs (딕셔너리)

def show_info(**info):
    for k, v in info.items():
        print(k, v)

show_info(name="Kim", age=20)


⸻

9. 매개변수 순서 규칙

일반 매개변수 → 기본값 → *args → **kwargs

def func(a, b=0, *args, **kwargs):
    pass


⸻

10. 지역 변수와 전역 변수

x = 10

def test():
    x = 20
    print(x)

test()
print(x)

	•	함수 내부 변수는 지역 변수
	•	전역 변수 수정은 권장하지 않음

global x

	•	사용은 가능하지만 지양

⸻

11. 함수 객체 개념

def hello():
    print("hi")

f = hello
f()

	•	함수도 객체
	•	변수에 할당 가능
	•	다른 함수의 인자로 전달 가능

⸻

12. 람다 함수 (익명 함수)

add = lambda a, b: a + b
print(add(3, 4))

	•	한 줄짜리 간단한 함수
	•	일회성 로직에 사용

⸻

13. 함수와 반복문 결합

def process(n):
    return n * 2

for i in range(5):
    print(process(i))


⸻

14. 함수 설계 원칙 (수업 포인트)
	•	함수는 하나의 역할만
	•	이름은 동사 형태
	•	입력과 출력이 명확해야 함
	•	print보다 return 중심 설계

⸻

15. 흔한 실수
	•	return 대신 print 사용
	•	함수 안에서 input 처리 남용
	•	전역 변수 의존

⸻

16. 수업용 핵심 요약
	•	함수는 코드 재사용 도구
	•	return은 값 반환
	•	매개변수 방식이 다양
	•	함수도 객체

⸻

17. 다음 단계
	•	함수 심화 (재귀 함수)
	•	함수 타입 힌트
	•	고차 함수 (map, filter)
	•	데코레이터 개념 소개

원하시면 다음도 바로 이어서 준비해드릴 수 있습니다.
- 함수 **실습 문제 세트**
- 함수 + 조건문/반복문 종합 문제
- lambda / map / filter 수업 자료
- Java 메서드와 비교 설명