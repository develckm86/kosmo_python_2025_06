_created: 2025-12-11 (update 날짜 적어주세요)_

# 파이썬 문자열(String) 정리
불변(immutable) 유니코드 시퀀스인 문자열의 기본 사용법과 주요 도구를 모았습니다.

## 1. 기본 개념과 생성
- 작은따옴표/큰따옴표 모두 사용, 여러 줄은 삼중따옴표.
```python
s1 = "Hello"
s2 = '안녕'
s3 = """여러 줄
문자열"""
```

## 2. 이스케이프·원시 문자열
```python
msg = "Hello\nWorld"   # 줄바꿈
path = r"C:\temp\file" # 원시 문자열, 백슬래시 그대로
text = "Hello's World" # 따옴표 이스케이프 대신 다른 따옴표 사용
```

## 3. 길이, 인덱싱, 슬라이싱
```python
s = "abcdefg"
len(s)       # 7
s[0], s[-1]  # 'a', 'g'
s[2:5]       # 'cde'
s[:3], s[3:] # 'abc', 'defg'
s[::2]       # 'aceg'
s[::-1]      # 'gfedcba' (역순)
```

## 4. 결합·반복·멤버십
```python
"Hello " + "Python"
"ha" * 3           # 'hahaha'
"py" in "python"   # True
```

## 5. 문자열 → 숫자 등 타입 변환
```python
i = 10
s = "i : " + str(i)
```

## 6. 포매팅
```python
name, score = "kim", 95
f"안녕 {name}, 점수 {score}"          # f-string (권장)
"안녕 {0}, 점수 {1}".format(name, score)
"안녕 %s, 점수 %d" % (name, score)    # 구식
```

## 7. 주요 메서드
```python
s = " Hello, World! "
s.upper(); s.lower()
s.strip()                # 앞뒤 공백 제거
s.replace("World", "Python")
s.split(",")             # [' Hello', ' World! ']
"-".join(["a", "b"])     # 'a-b'
s.find("World")          # 없으면 -1
s.startswith(" Hello"); s.endswith("!")
s.count("o")
```

## 8. 정규표현식 요약
```python
import re
t = "age 20 height 180"
re.match("he", "hello")         # 시작 일치
re.search("py", "hello python") # 전체 검색
re.findall(r"\d+", t)           # ['20', '180']
re.fullmatch(r"\d{3}-\d{4}", "010-1234")
```

## 9. 불변성
```python
s = "hello"
# s[0] = "H"  # 불가, 새 문자열로 만들어야 함
s = "H" + s[1:]
```

## 10. 바이트와 인코딩
```python
b = "안녕".encode("utf-8")  # bytes, 불변
print(b, b[0])             # b'\\xec\\95\\88\\xeb\\85\\95' 236
text = b.decode("utf-8")   # '안녕'

ba = bytearray(b)          # 가변 바이트 시퀀스
ba[0] = 0x41
```

## 11. 연습 아이디어
- 사용자 입력을 받아 공백 제거 후 대문자/소문자 변환하기.
- 슬라이싱으로 문자열 앞/뒤/짝수 위치 문자 추출하기.
- `split`/`join`으로 CSV 한 줄을 리스트로 바꾼 뒤 다시 문자열로 만들기.
