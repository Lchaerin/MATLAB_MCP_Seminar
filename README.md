# POSTECH 세미나 — Agentic AI로 MATLAB·Simulink 효율화하기: 실습 자료

AI 에이전트를 MATLAB MCP Server로 MATLAB·Simulink에 연결해, 데이터 분석·모델 디버깅·딥러닝 객체 검출을 함께 해 보는 실습입니다.

[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=Lchaerin/MATLAB_MCP_Seminar&file=Lab02_NIR_Spectra_Analysis.m)

## 구성

| 파일 / 폴더 | 내용 |
|---|---|
| `Lab02_NIR_Spectra_Analysis.m` | 실습 2: NIR 분광 데이터 분석 (MATLAB) |
| `Lab03_HouseHeating_Simulink.m` + `Lab03_HouseHeating/` | 실습 3: 집 난방 Simulink 모델 분석·디버깅·검증 |
| `Lab04_YOLO_Vehicle_Detection.m` | 실습 4: SqueezeNet 전이학습으로 YOLO v2 차량 검출기 만들고 검증하기 |
| `AGENTS.md`, `CLAUDE.md` | AI 에이전트 작업 규칙 (수정하지 마세요) |

## 준비

1. 위의 **Open in MATLAB Online** 버튼을 누르고 MathWorks 계정으로 로그인합니다(MATLAB Online R2025a 이상).
   실습 자료가 **본인 MATLAB Drive**에 복사되고 실습 2 파일이 열립니다. 복사본은 본인 것이라 마음대로 고쳐도 됩니다.
   - 버튼을 쓸 수 없으면 이 페이지의 **Code → Download ZIP**으로 받아 MATLAB Drive에 올리고, 명령 창에서 `unzip`으로 압축을 풉니다.
2. 실습 파일이 들어 있는 폴더를 **현재 폴더**로 설정합니다(현재 폴더 창에서 그 폴더를 더블클릭). 각 실습의 0단계는 현재 폴더에 실습 파일이 있는지 확인하고, 없으면 멈춥니다.
3. 실습별로 필요한 제품이 있는지 확인합니다.
   - 실습 2: Statistics and Machine Learning Toolbox
   - 실습 3: Simulink, Stateflow, Simscape
   - 실습 4: Deep Learning Toolbox, Computer Vision Toolbox, Image Processing Toolbox (별도 애드온 불필요, CPU로 학습)
4. 명령 창에서 `shareMATLABSession`을 실행한 뒤, **이 폴더를 작업 폴더로 하여** AI 에이전트(Codex, Claude Code 등)를 시작합니다.

## 진행 방법

- 실습 2 → 3 → 4 순서로 진행합니다. 각 실습 파일을 열고 **섹션 단위로 하나씩 실행**(Ctrl+Enter)하세요.
- 각 실습의 0단계에 있는 **첫 프롬프트**를 에이전트에게 먼저 보내세요. 에이전트가 만든 코드는 `Lab02_agent_work.m`처럼 실습별 **작업 노트** 라이브 스크립트에 기록되고 편집기에 열립니다.
- 프롬프트가 있는 섹션을 실행하면 프롬프트가 클립보드에 복사됩니다. 복사가 안 되면 본문의 프롬프트를 직접 복사해 붙여 넣으세요.

## 꼭 지켜 주세요

- AI가 만든 코드와 결과는 **초안**입니다. 검토하고, 실행하고, 테스트하고, 이해한 뒤에 사용하세요. 결과에 대한 책임은 사용자에게 있습니다.
- 기밀·개인 정보·미공개 연구 데이터, 비밀번호나 API 키를 프롬프트에 넣지 마세요.
- 이해하지 못한 명령이나 변경은 승인하지 마세요.

## 출처와 라이선스

- 실습 3은 MathWorks의 MATLAB EXPO 2026 "Agentic AI Hands-On Workshop" Simulink 실습을 바탕으로 만들었습니다.
- 실습 4의 차량 사진과 정답 라벨은 Computer Vision Toolbox에, 사전학습 신경망 SqueezeNet은 Deep Learning Toolbox에 들어 있습니다.
- 실습 2의 데이터는 Statistics and Machine Learning Toolbox의 예제 데이터(`spectraTable`)를 사용하며, 실행 중에 자동으로 준비됩니다.
