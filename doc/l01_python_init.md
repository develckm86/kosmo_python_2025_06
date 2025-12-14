_created: 2025-12-11 (update 날짜 적어주세요)_

# 파이썬 소개와 개발 환경 준비
파이썬의 특징과 설치, 가상환경, VS Code 설정, 단축키를 한 번에 정리했습니다.

## 1. 파이썬 한눈에 보기
- 1991년 귀도 반 로섬이 만든 고급 언어. 문법이 단순해 입문·교육에 적합.
- 주요 활용: 웹 백엔드, 데이터 분석·머신러닝, 자동화 스크립트, 네트워크/서버, 교육.
- 모두 객체로 취급하고 방대한 표준/서드파티 라이브러리 생태계를 보유.

## 2. 언어 특징
- 읽기 쉬운 문법(들여쓰기 기반), 동적 타이핑, 인터프리터 실행.
- 객체 지향/절차/함수형 패러다임을 모두 지원.
- 바이트코드( .pyc )를 생성해 가상 머신(PyVM)에서 실행.

## 3. 패키지·환경 관리 도구
- **pip**: 기본 패키지 관리자. `pip install requests`
- **venv**: 표준 가상환경. 프로젝트별 격리.
  ```bash
  python -m venv venv
  source venv/bin/activate        # Windows는 venv\Scripts\activate
  ```
- **conda**: 데이터 분석/과학 분야에서 인기. 파이썬 외 시스템 패키지도 함께 관리.
- 선택 기준: 일반 개발은 `pip + venv`, 복잡한 데이터/ML 스택은 `conda`.

## 4. 설치와 버전 확인
- 공식 다운로드: https://www.python.org/downloads/
- Windows 설치 시 “Add Python to PATH” 체크.
- 설치 확인
  ```bash
  python --version
  pip --version
  ```

## 5. VS Code로 개발 환경 세팅
- 필수 확장: **Python**, **Pylance**. 코드 포매팅은 **Black Formatter** 권장.
- 장고 등 웹 개발 시: **Django**, **Django Template**(선택).
- 프로젝트 열기: 원하는 폴더 생성 후 VS Code에서 `File → Open Folder`.
- 가상환경 생성/활성화 후 VS Code 좌측 하단의 Python 버전을 클릭해 `venv` 인터프리터를 선택.

## 6. VS Code 단축키 모음

### 편집
| 기능 | Windows | macOS |
|------|---------|--------|
| 줄 복사 | Shift + Alt + ↓ / ↑ | Shift + Option + ↓ / ↑ |
| 줄 이동 | Alt + ↓ / ↑ | Option + ↓ / ↑ |
| 줄 삭제 | Ctrl + Shift + K | Command + Shift + K |
| 줄 주석 | Ctrl + / | Command + / |
| 블록 주석 | Shift + Alt + A | Shift + Option + A |
| 여러 커서 | Alt + 클릭 | Option + 클릭 |
| 자동 정렬 | Shift + Alt + F | Shift + Option + F |

### 파일/탭
| 기능 | Windows | macOS |
|------|---------|--------|
| 파일 열기 | Ctrl + O | Command + O |
| 새 파일 | Ctrl + N | Command + N |
| 파일 저장 | Ctrl + S | Command + S |
| 모두 저장 | Ctrl + K, S | Command + Option + S |
| 탐색기 토글 | Ctrl + B | Command + B |
| 탭 이동 | Ctrl + Tab | Control + Tab |
| 탭 닫기 | Ctrl + W | Command + W |

### 검색/치환
| 기능 | Windows | macOS |
|------|---------|--------|
| 전체 검색 | Ctrl + Shift + F | Command + Shift + F |
| 현재 파일 검색 | Ctrl + F | Command + F |
| 현재 파일 치환 | Ctrl + H | Command + Option + F |
| 다음/이전 결과 | F4 / Shift + F4 | F4 / Shift + F4 |
