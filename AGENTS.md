# 실습 폴더 작업 규칙 (AI 에이전트용)

이 폴더는 MATLAB·Simulink 실습 폴더입니다. 실습생이 에이전트가 만든 코드를 **라이브 스크립트에서 직접 읽고 다시 실행**할 수 있어야 합니다. MATLAB 코드를 만들거나 실행할 때, Simulink 모델을 바꿀 때는 아래 규칙을 반드시 따르세요.

## 1. 코드는 먼저 작업 노트에 적는다

- 실습마다 작업 노트가 하나씩 있습니다. 실습생이 알려준 실습 번호를 따라 이름을 정합니다.
  - 실습 2(NIR 분광 데이터): `Lab02_agent_work.m`
  - 실습 3(집 난방 Simulink 모델): `Lab03_agent_work.m`
  - 실습 4(YOLO 차량 검출): `Lab04_agent_work.m`
- 이 실습에서 작성하는 모든 MATLAB 코드는 해당 작업 노트(plain text 라이브 스크립트)에 **새 섹션으로 먼저 적은 뒤** 실행합니다. 코드를 적지 않고 MCP로만 실행하지 마세요.
- 작업 노트가 없으면 아래 내용으로 새로 만듭니다(`NN`은 실습 번호).

```matlab
%[text] # 실습 NN 작업 노트 — AI 에이전트가 작성한 코드
%[text] AI 에이전트가 실행한 코드를 순서대로 기록한 파일입니다. 각 섹션을 직접 실행(Ctrl+Enter)해 결과를 확인하세요.

%[appendix]{"version":"1.0"}
%---
%[metadata:view]
%   data: {"layout":"inline"}
%---
```

- 섹션 형식: `%%` 줄 → `%[text] ## 단계 제목` → 무엇을 하는지 한두 문장(`%[text]`) → 코드. 코드 주석은 한국어로 짧게 씁니다.
- 라이브 스크립트 형식은 MATLAB MCP Server의 리소스 `plain_text_live_code_guidelines`를 따릅니다.

## 2. 기존 내용을 지키며 추가한다

- 새 섹션은 파일 끝의 `%[appendix]` 줄 **바로 앞**에 넣습니다. `%[appendix]` 아래 내용은 절대 건드리지 마세요.
- 이미 있는 섹션을 지우거나 덮어쓰지 않습니다. 오류를 고칠 때는 해당 섹션만 수정하고, 무엇을 왜 바꿨는지 설명합니다.
- 코드 줄 끝의 `%[output:...]` 표시는 지우지 않습니다(MATLAB이 저장한 실행 결과 연결 표시입니다).

## 3. 파일을 띄우고, 적힌 코드 그대로 실행한다

1. 작업 노트를 저장한 뒤 `evaluate_matlab_code`로 아래 코드를 실행해 실습생의 편집기에 띄웁니다(`NN`은 실습 번호). 편집기는 디스크의 변경을 자동으로 다시 불러오지 않으므로 `reload`가 꼭 필요합니다.

   ```matlab
   d = matlab.desktop.editor.openDocument(fullfile(pwd, "LabNN_agent_work.m"));
   if d.Modified
       disp("편집기에 저장하지 않은 변경이 있습니다. 실습생에게 저장(Ctrl+S)을 요청하세요.")
   else
       d.reload;
   end
   ```

   저장하지 않은 변경이 있다는 메시지가 나오면, 실습생에게 저장을 요청한 뒤 다시 실행합니다. 실습생이 직접 고친 내용을 덮어쓰지 마세요.
2. 방금 추가한 섹션의 코드를 **파일에 적힌 것과 똑같이** `evaluate_matlab_code`로 실행합니다. 앞 섹션에서 만든 변수는 같은 MATLAB 세션에 남아 있으므로 섹션 단위로 실행하면 됩니다.
3. 오류가 나면 작업 노트의 해당 섹션을 고친 뒤 다시 실행합니다. 파일 내용과 실제로 실행한 코드가 항상 같아야 합니다.

## 4. Simulink 모델을 다룰 때 (실습 3)

- 모델을 읽고 고칠 때는 Simulink MCP 도구(`model_overview`, `model_read`, `model_edit`, `model_check` 등)를 사용합니다.
- 모델을 바꿨다면 작업 노트에 **텍스트 섹션**으로 무엇을 바꿨는지(블록 경로, 바꾼 파라미터, 추가한 블록과 연결) 적고, 변경을 확인하는 MATLAB 코드(시뮬레이션, 테스트 실행 등)를 이어서 적습니다.
- 변경 후 `model_check`로 연결 상태를 확인하고, 시뮬레이션이나 테스트로 검증한 뒤 `save_system`으로 저장합니다.
- 시뮬레이션 결과를 분석할 때는 필요한 신호의 로깅을 켜고 `sim`의 출력(`logsout`)을 사용합니다.
- 테스트는 Simulink Test 대신 `matlab.unittest` 테스트 클래스로 만들고, 시뮬레이션 결과로 요구사항을 판정합니다(MATLAB Online에서는 Simulink Test를 쓸 수 없습니다). 실행은 `run_matlab_test_file`로 합니다.

## 5. 함수와 테스트

- 재사용 함수와 `matlab.unittest` 테스트 클래스는 별도 `.m` 파일로 만들고, 작업 노트에는 그것을 호출하거나 `run_matlab_test_file`로 실행하는 섹션을 적습니다.

## 6. 손대지 않을 파일

- 실습 안내 파일(`Lab02_NIR_Spectra_Analysis.m`, `Lab03_HouseHeating_Simulink.m`, `Lab04_YOLO_Vehicle_Detection.m`)은 수정하지 않습니다.
- `*_Solution.m` 파일과 `Lab02_solution`, `Lab03_solution`, `Lab04_solution` 폴더가 있더라도 열거나 참고하지 않습니다(강사용 정답).
