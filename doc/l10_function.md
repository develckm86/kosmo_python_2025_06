# 파이썬 함수(Function) 정리

## 1. 기본 정의와 호출
- `def`로 이름, 매개변수, 본문을 선언하고 `return`으로 결과를 돌려준다. `return`이 없으면 `None`.
```python
def sum(a, b):
    return a + b

print(sum(10, 20))  # 30
```
- 같은 이름의 함수를 다시 정의하면 **마지막 정의가 이전 정의를 덮어쓴다**. (예: `sum(a,b)` 뒤에 `sum(a,b,c)`를 만들면 이후엔 3개 인자 버전만 사용 가능)

## 2. 가변 인자와 언패킹
- `*args`는 가변 개수의 위치 인자를 **튜플**로 받는다.
```python
def sum_all(*args):
    print(args)          # 전달된 값이 튜플로 모인다
    total = 0
    for n in args:
        total += n
    return total

print(sum_all(10, 20, 30))
nums = [100, 200, 300]
print(sum_all(*nums))    # 리스트를 *로 풀어 전달
```
- `**kwargs`는 키워드 인자를 **딕셔너리**로 받는다.
```python
def student_info(**student):
    print(student)                 # {'name': '경민', 'age': 39}
    print(f"name={student['name']}")
    print(f"age={student['age']}")

student_info(name="경민", age=39)
stu = {"name": "지형", "age": 28}
student_info(**stu)                # dict도 **로 풀어 전달
```
- 키워드 인자 언패킹은 호출부에서도 활용할 수 있다.
```python
def student_say(name, age):
    print(f"{name}의 나이는 {age} 입니다")

student_say(**{"name": "지형", "age": 35})
```

## 3. 반환값과 튜플 언패킹
- 여러 값을 반환하면 내부적으로 **튜플**이 만들어진다. 필요하면 한 번에 언패킹.
```python
def calc(a, b):
    return a + b, a - b

result = calc(10, 20)
print(result, type(result))  # (30, -10) <class 'tuple'>
a_plus_b, a_minus_b = calc(5, 2)
```

## 4. 람다와 함수 객체
- 람다(lambda)는 이름 없는 한 줄 함수 표현식.
```python
add = lambda a, b: a + b
print(add(10, 20))
```
- 함수는 **객체**이므로 변수에 할당하거나 다른 함수에 넘길 수 있다.
```python
def sum(a, b):
    return a + b

print(sum)  # <function sum at ...>
f = sum
print(f(1, 2))
```

## 5. 지역 변수와 전역 변수
- 함수 안에서 만든 변수는 함수가 끝나면 사라지는 **지역 변수**, 파일 상단에 둔 변수는 어디서나 읽을 수 있는 **전역 변수**.
- 함수 안에서 전역 변수를 읽을 때는 그냥 사용 가능하지만, 값을 바꾸려면 `global` 선언이 필요하다. (가능하면 전역 수정은 최소화)
```python
x = 10  # 전역 변수

def show_numbers():
    x = 20  # 지역 변수
    print("함수 안 x:", x)

show_numbers()
print("함수 밖 x:", x)  # 전역 x는 그대로

def change_global():
    global x
    x = 99  # 전역 값 수정

change_global()
print("전역 x 수정 후:", x)
```

