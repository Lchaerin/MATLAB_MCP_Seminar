# POSTECH 세미나 — Agentic AI로 MATLAB·Simulink 효율화하기: 실습 자료

AI 에이전트를 MATLAB MCP Server로 MATLAB·Simulink에 연결해, 데이터 분석·모델 디버깅·딥러닝 객체 검출을 함께 해 보는 실습입니다.

[![Open MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://www.mathworks.com/licensecenter/classroom/5606200/)

## 구성

| 파일 / 폴더 | 내용 |
|---|---|
| `Lab02_NIR_Spectra_Analysis.m` | 실습 2: NIR 분광 데이터 분석 (MATLAB) |
| `Lab03_HouseHeating_Simulink.m` + `Lab03_HouseHeating/` | 실습 3: 집 난방 Simulink 모델 분석·디버깅·검증 |
| `Lab04_YOLO_Vehicle_Detection.m` | 실습 4: SqueezeNet 전이학습으로 YOLO v2 차량 검출기 만들고 검증하기 |
| `AGENTS.md`, `CLAUDE.md` | AI 에이전트 작업 규칙 (수정하지 마세요) |

## 준비

1. 위의 **Open MATLAB Online** 버튼을 눌러 워크샵 라이센스로 매트랩 온라인에 접속합니다. (로그인 필요)
2. 이 페이지의 **Code → Download ZIP**으로 받아 MATLAB Drive에 올리고, 명령 창에서 `unzip`으로 압축을 풉니다.
3. 실습 파일이 들어 있는 폴더를 **현재 폴더**로 설정합니다(현재 폴더 창에서 그 폴더를 더블클릭). 각 실습의 0단계는 현재 폴더에 실습 파일이 있는지 확인하고, 없으면 멈춥니다.
4. 실습별로 필요한 제품이 있는지 확인합니다.
   - 실습 2: Statistics and Machine Learning Toolbox
   - 실습 3: Simulink, Stateflow, Simscape
   - 실습 4: Deep Learning Toolbox, Computer Vision Toolbox, Image Processing Toolbox (별도 애드온 불필요, CPU로 학습)
5. 명령 창에서 `shareMATLABSession`을 실행한 뒤, **이 폴더를 작업 폴더로 하여** AI 에이전트(Codex, Claude Code 등)를 시작합니다.
