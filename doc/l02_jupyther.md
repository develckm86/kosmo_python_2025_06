_created: 2025-12-11 (update 날짜 적어주세요)_

# Jupyter Notebook(.ipynb) vs Python Script(.py)
노트북과 스크립트의 차이, VS Code에서 노트북을 쓰는 법을 정리했습니다.

## 1. 노트북(.ipynb)
- 코드·결과·설명을 한 문서에 담는 인터랙티브 환경.
- 셀 단위 실행, 그래프/표를 즉시 확인, Markdown·수식 작성 가능.
- 장점: 실험과 시각화에 유리, 강의/보고서에 적합.  
  단점: 실행 순서 꼬임 위험, 큰 프로젝트 diff/리뷰가 어려움.

## 2. 스크립트(.py)
- 파일 전체를 위에서 아래로 실행, 함수/클래스/패키지 구조화에 유리.
- 장점: 유지보수·버전관리 최적, 서비스/백엔드/패키지 개발 표준.  
  단점: 문서 안에서 즉시 그래프를 보긴 어렵다.

## 3. 언제 무엇을 쓸까?
| 상황 | 권장 |
|------|------|
| 데이터 분석, ML 실험, 시각화 | `.ipynb` |
| 웹/서버/API 개발, 패키지화 | `.py` |
| 알고리즘 풀이 | `.py` |
| 코드+설명+결과를 한 번에 담고 싶을 때 | `.ipynb` |

## 4. VS Code에서 노트북 사용
- 필수 확장: **Python**, **Jupyter**.  
  선택: **Jupyter Keymap**, **Jupyter Notebook Renderers**.
- 실행 절차  
  1) `.ipynb` 파일 열기 → 자동 Jupyter UI.  
  2) “Select Kernel”에서 사용할 Python(venv 권장) 선택.  
  3) 셀 옆 실행 버튼 ▶ 또는 `Shift+Enter`로 실행.
- 새 노트북 만들기  
  1) Command Palette(`Ctrl+Shift+P` / `Cmd+Shift+P`) → `Jupyter: Create New Blank Notebook`.  
  2) Kernel 선택 후 셀 추가/실행.
- 자주 쓰는 셀 단축키: `Shift+Enter` 실행, `A/B` 셀 추가, `M`/`Y`로 Markdown/Code 전환, `DD` 삭제, “Run All”로 전체 실행.

## 5. 요약
| 비교 | Notebook(.ipynb) | Script(.py) |
|------|------------------|-------------|
| 실행 | 셀 단위 | 파일 전체 |
| 시각화 | 문서 안에 직접 표시 | 별도 창/콘솔 |
| 강점 | 실험·학습·보고서 | 구조화·버전관리·배포 |
| VS Code | Python + Jupyter 확장 필요 | Python 확장만 필요 |
