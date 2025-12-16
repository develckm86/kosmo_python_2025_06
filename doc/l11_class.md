# 파이썬 클래스(class) 정리

## 1. 클래스와 인스턴스
- 클래스: 객체를 만들기 위한 설계도, `class` 키워드로 정의.
- 인스턴스: 클래스로부터 생성된 실제 객체.
```python
class Person:
    pass

p = Person()  # 인스턴스 생성
```

## 2. 속성, 메서드, self
- `self`는 인스턴스 자신을 가리키며, 인스턴스 메서드 첫 매개변수 이름으로 관례적으로 사용(예약어가 아니라 관례).
```python
class Person:
    def __init__(self, name, age):  # 생성자
        self.name = name            # 인스턴스 변수
        self.age = age

    def intro(self):                # 인스턴스 메서드
        print(f"{self.name}, {self.age}")

p = Person("Kim", 20)
p.intro()
```

## 3. 클래스 변수 vs 인스턴스 변수
- 클래스 변수: **클래스에 1개만 존재**하며 모든 인스턴스가 공유. `ClassName.var`로 읽고 쓴다. 인스턴스에서 `self.var`로 덮어쓰면 같은 이름의 인스턴스 변수가 생겨 클래스 변수와 분리된다.
- 인스턴스 변수: **인스턴스마다 별도 보관**. 보통 `__init__`에서 `self.var`로 생성한다.
```python
class Counter:
    total = 0  # 클래스 변수

    def __init__(self):
        self.count = 0   # 인스턴스 변수
        Counter.total += 1

c1 = Counter()
c2 = Counter()
print(Counter.total)  # 2
print(c1.count, c2.count)
# 인스턴스마다 count는 따로, total은 모두 공유
```

## 4. 메서드 종류
- 인스턴스 메서드: `self`로 인스턴스 상태를 다룸. 가장 일반적인 메서드 형태.
- 클래스 메서드: `@classmethod`, 첫 인자로 `cls`(클래스 자체). **클래스 변수 변경**이나 **대안 생성자**(여러 입력 형식을 받아 객체 생성) 구현에 적합. 인스턴스 없이도 `ClassName.method()`로 호출.
- 정적 메서드: `@staticmethod`, `self`/`cls` 미사용. 클래스와 연관된 **순수 함수**를 클래스 이름 아래 묶을 때 사용. 상태를 건드리지 않는 계산/도구성 함수에 적합.
```python
class MathTool:
    unit = "cm"

    @classmethod
    def change_unit(cls, u):
        cls.unit = u

    @classmethod
    def from_meter(cls, value_m):
        inst = cls()
        inst.value = value_m * 100
        return inst

    @staticmethod
    def add(a, b):
        return a + b
```

### Java 기준으로 한 번에 이해하기 (static vs classmethod vs staticmethod)
- 요약: Java의 `static`을 파이썬이 **의도별로 둘로 쪼개서** `@classmethod`와 `@staticmethod`로 표현.

#### 1) Java static 메서드 (한 종류)
```java
public class MathTool {
    static String unit = "cm";

    static int add(int a, int b) {
        return a + b;
    }
}
```
- 특징: 객체 없이 호출, 클래스 변수 접근 가능, 인스턴스 변수 접근 불가.

#### 2) Python classmethod (@classmethod)
- 의미: Java static 중에서도 **클래스 자체를 다루는 것**을 담당.  
- 특징: 첫 인자 `cls`(클래스 자신), 클래스 변수 접근/변경 가능, 객체 생성 로직(팩토리)에서 자주 사용, 상속 시 자식 클래스 기준으로 동작.  
- Java 대응 감각: `static` 메서드에서 `this` 대신 `ClassName`을 받는 느낌.
```python
@classmethod
def change_unit(cls, u):
    cls.unit = u
```
```java
// 대응 개념
static void changeUnit(String u) {
    unit = u;
}
```

#### 3) Python staticmethod (@staticmethod)
- 의미: Java static 중에서도 **클래스와 이름만 묶인 순수 함수**.  
- 특징: `self` 없음, `cls` 없음, 클래스 변수도 건드리지 않음. 위치만 클래스 안에 둘 뿐.  
```python
@staticmethod
def add(a, b):
    return a + b
```
```java
// 대응 개념
static int add(int a, int b) {
    return a + b;
}
```

#### 4) 한 줄 요약
- Java: `static` 하나로 다 처리.
- Python: `classmethod`(클래스 상태/생성) + `staticmethod`(상태 무관 유틸)로 의도를 분리.

#### 5) 한눈에 비교 표

| 구분               | Java static | Python classmethod | Python staticmethod |
|-------------------|-------------|--------------------|---------------------|
| 객체 없이 호출     | 가능        | 가능               | 가능                |
| 클래스 변수 접근   | 가능        | 가능               | 보통 안 함          |
| 인스턴스 접근      | 불가        | 불가               | 불가                |
| 첫 인자            | 없음        | cls                | 없음                |
| 주 용도            | 범용        | 클래스 상태/생성    | 유틸 함수           |


## 5. 특수 메서드(매직 메서드) 핵심 정리
### 1) 정의
- 이름에 앞뒤로 밑줄이 있는 메서드(`__add__`, `__len__` 등).  
- 파이썬 문법이 객체를 사용할 때 자동 호출되어 **연산자/반복/출력** 같은 동작을 연결한다.  
- 예: `len(obj) -> __len__`, `obj1 + obj2 -> __add__`, `obj1 == obj2 -> __eq__`, `for x in obj -> __iter__`와 `__next__`.

### 2) 객체 생성과 소멸
- `__init__(self, ...)`: 객체가 만들어진 직후 호출, 인스턴스 변수 초기화.  
- `__del__(self)`: 객체 소멸 훅. 정확한 호출 시점을 장담하기 어렵고 실무에서는 거의 사용하지 않는다.
```python
class User:
    def __init__(self, name):
        self.name = name
```

### 3) 객체 출력
- `__str__(self)`: `print(obj)` 때 사용, 사람이 읽기 좋은 문자열.  
- `__repr__(self)`: 디버깅용 정확한 표현. 인터프리터 프롬프트나 `repr(obj)` 호출에 사용(없으면 기본 구현이 표시됨).

### 4) 연산자 오버로딩
- 연산자를 객체 동작으로 확장할 때 구현.  
- 자주 쓰는 것: `__add__(+)`, `__eq__(==)`, `__lt__(<)`, 필요 시 `__sub__`, `__mul__`, `__hash__` 등.
```python
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y
    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
    def __eq__(self, other):
        return (self.x, self.y) == (other.x, other.y)
    def __str__(self):
        return f"({self.x}, {self.y})"
```

### 5) 컨테이너와 반복
- `__len__`: `len(obj)` 지원.  
- `__getitem__`: `obj[index]` 지원.  
- `__iter__`와 `__next__`: `for` 문에서 순회 가능하게 만든다(이터레이터 프로토콜).

### 6) with 문(컨텍스트 매니저)
- `__enter__`: `with` 블록 시작 시 호출.  
- `__exit__`: `with` 블록 종료 시 호출, 자원 정리/마무리 작업 수행.

## 6. 상속과 오버라이딩
- 상속: 부모 기능을 물려받아 재사용/확장.
- 오버라이딩: 같은 이름 메서드를 새로 정의해 동작 변경.
- `super()`로 부모 초기화나 메서드 호출.
```python
class Animal:
    def __init__(self, name):
        self.name = name
    def speak(self):
        print("...")  # 기본 동작

class Dog(Animal):
    def __init__(self, name, kind):
        super().__init__(name)
        self.kind = kind
    
    def speak(self):   # 오버라이딩
        print("멍멍")
```

## 7. 최상위 부모(object)
- 파이썬 3에서 **모든 클래스는 자동으로 `object`를 상속**한다. (`class A: pass` == `class A(object): pass`)
- `object`가 제공하는 기본 메서드: `__str__`, `__repr__`, `__eq__`, `__hash__`, `__class__` 등.
- 커스텀 동작을 원하면 필요한 매직 메서드만 선택적으로 오버라이드한다.

## 8. 캡슐화와 네이밍 관례
- 언더스코어로 의도를 표현: `_name`(내부용), `__name`(네임맹글링: 클래스 내부에서만 주로 사용).
- 완전한 접근 제어는 아니며, 파이썬은 "규칙을 존중"하는 철학에 가깝다.
