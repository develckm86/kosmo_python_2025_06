# 파이썬 반복문(for)과 다양한 반복 방식 정리

## 1. 반복문 개요
- 반복문은 **여러 번 같은 작업을 수행**할 때 사용
- 파이썬에서는 주로 `for` 반복문 사용
- 컬렉션, 시퀀스, 이터레이터 기반 반복이 핵심

---

## 2. for 반복문 기본 구조
```python
for 변수 in 반복가능객체:
    실행문

	•	반복가능객체(iterable)
	•	list, tuple, dict, set
	•	문자열
	•	range
	•	iterator 객체

for i in [1, 2, 3]:
    print(i)


⸻

3. 시퀀스(sequence) 기반 반복
	•	시퀀스
	•	순서가 있는 자료형
	•	list, tuple, str, range

리스트 반복

nums = [10, 20, 30]

for n in nums:
    print(n)

튜플 반복

point = (3, 5)

for v in point:
    print(v)

문자열 반복

word = "python"

for ch in word:
    print(ch)

range 반복

for i in range(5):
    print(i)

for i in range(1, 10, 2):
    print(i)


⸻

4. 컬렉션별 반복 방식

list 반복

scores = [80, 90, 70]

for s in scores:
    print(s)


⸻

tuple 반복

colors = ("red", "green", "blue")

for c in colors:
    print(c)


⸻

dict 반복
	•	key 기준 반복

student = {"name": "kim", "age": 20}

for key in student:
    print(key)

	•	value 기준 반복

for value in student.values():
    print(value)

	•	key, value 동시 반복

for key, value in student.items():
    print(key, value)


⸻

set 반복

nums = {1, 2, 3}

for n in nums:
    print(n)

	•	순서가 보장되지 않음

⸻

5. 인덱스가 필요한 반복

range + len

data = ["a", "b", "c"]

for i in range(len(data)):
    print(i, data[i])

enumerate 사용 (권장)

for idx, value in enumerate(data):
    print(idx, value)

	•	인덱스와 값을 동시에 제공
	•	가독성 우수

⸻

6. 다중 시퀀스 반복

zip 사용

names = ["kim", "lee", "park"]
scores = [90, 80, 70]

for name, score in zip(names, scores):
    print(name, score)

	•	가장 짧은 시퀀스 기준으로 반복

⸻

7. 이터레이터(iterator) 개념
	•	반복 가능한 객체에서 하나씩 값을 꺼내는 객체
	•	__iter__() 와 __next__() 구현

iterator 생성

nums = [1, 2, 3]
it = iter(nums)

next 사용

print(next(it))
print(next(it))
print(next(it))

	•	더 이상 값이 없으면 StopIteration 발생

⸻

8. for 문과 iterator의 관계
	•	for 문 내부 동작 개념

it = iter(nums)
while True:
    try:
        value = next(it)
        print(value)
    except StopIteration:
        break

	•	for 문은 iterator를 자동 처리

⸻

9. 중첩 for 문

for i in range(3):
    for j in range(2):
        print(i, j)

	•	2차원 데이터 처리에 사용

⸻

10. break / continue
	•	break
	•	반복 즉시 종료

for i in range(10):
    if i == 5:
        break
    print(i)

	•	continue
	•	현재 반복만 건너뜀

for i in range(5):
    if i == 2:
        continue
    print(i)


⸻

11. for - else 구문
	•	반복이 정상 종료되었을 때 else 실행

for i in range(5):
    if i == 10:
        break
else:
    print("끝까지 반복됨")


⸻

12. 컴프리헨션 맛보기
	•	리스트 컴프리헨션

squares = [x * x for x in range(5)]

	•	조건 포함

evens = [x for x in range(10) if x % 2 == 0]


⸻

13. 반복문 선택 기준
	•	단순 반복
	•	for + 컬렉션
	•	인덱스 필요
	•	enumerate
	•	여러 컬렉션 동시 처리
	•	zip
	•	대용량/지연 처리
	•	iterator
	•	결과 리스트 생성
	•	컴프리헨션

⸻

14. 실습 문제 예시
	•	리스트 요소 합계 계산
	•	딕셔너리 key/value 출력
	•	enumerate로 순번 붙이기
	•	zip으로 성적표 출력
	•	break를 이용한 검색 로직

⸻

15. 다음 단계
	•	while 반복문
	•	컴프리헨션 심화
	•	generator
	•	map / filter 함수

원하시면  
- 반복문 **실습 문제 md 10~20문제**
- iterator / generator **심화 수업**
- for + if + 컬렉션 **종합 문제**

바로 이어서 정리해드릴게요.