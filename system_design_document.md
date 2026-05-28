# 시스템 설계 문서 (System Design Document)

- **과업명**: 지능형 회의 요약 및 액션 아이템 추출 시스템 (Intelligent Meeting Summarizer & Action Item Extractor)
- **대상 모델**: Claude Opus 4.7 (최종 선정 모델)
- **작성일**: 2026-05-28
- **작성자**: 코디세이 AI 네이티브 과정 퍼실리테이터

---

## 1. 문제 정의 및 목표 (Problem Definition & Objectives)

### 1.1. 타겟 사용자 (Target Audience)
- 프로젝트 매니저(PM), 스크럼 마스터(Scrum Master), 팀 리드 및 에이전트 워크플로우를 통해 수많은 미팅 내용을 정제해야 하는 비즈니스 전문가.

### 1.2. 입력 데이터 형태 (Input Data Format)
- 정제되지 않은 회의 대화 스크립트(Raw Audio Transcription) 또는 자유 형식의 회의 메모 텍스트.

### 1.3. 출력 규격 (Output Specifications)
- Markdown 형식을 철저히 준수한 구조적 보고서. 아래의 표준 포맷으로 출력되어야 합니다:
  1. **개요 (Overview)**: 회의 주제, 목적 및 핵심 상황 요약 (3줄 이내).
  2. **핵심 결정사항 (Key Decisions)**: 합의된 사항들의 리스트.
  3. **액션 아이템 (Action Items)**: [업무 범위 / 담당 역할 / 마일스톤 기한]을 명확히 명시한 불릿 리스트.
  4. **미결 이슈 및 확인 필요 (Open Issues / Verification Required)**: 정보가 부족하거나 모호하여 환각을 피하기 위해 보류한 항목 리스트.

---

## 2. 업무 과업 입력 템플릿 (Re-usable Input Template)

실무자가 매번 복사하여 재사용할 수 있는 표준 입력 템플릿(Standard Input Template)입니다.

```text
[Input Template]
=========================================
[Meeting Transcript]
(여기에 원시 대화 내용 또는 회의 요약 메모를 입력하세요)

[Focus Areas]
- Key Goals: (예: 병목 구간 파악, 일정 관리)
- Priority: (예: 일정 우선, 기술 리스크 최소화)

[Constraints]
- Replace real names with role names (e.g., PM, Developer, Lead).
- Do NOT generate speculative action items.
- If information is insufficient, put it in the [Verification Required] section.
=========================================
```

---

## 3. 페르소나 및 시스템 프롬프트 설계 (Persona & System Prompt)

### 3.1. 페르소나 정의 (Persona Definition)
- **이름/역할**: 시니어 테크니컬 PM & Agile 코치 (Aiden)
- **전문 분야**: 복잡한 비즈니스 대화 맥락 분석, 작업 단위(Task Breakdowns) 세분화, 애자일 마일스톤 관리.
- **말투/톤앤매너**: 간결하고 격식 있으며 명확한 비즈니스 어조(Professional & Objective).
- **최우선순위**: **정확성(Accuracy)과 안전성(Safety)**. 추정치나 누락된 일정을 자의적으로 해석하여 생성하지 않음.

### 3.2. 시스템 프롬프트 전문 (System Prompt Blueprint)

```text
[System Prompt - Aiden]
You are a highly experienced Senior Technical Project Manager and Agile Facilitator. 
Your goal is to analyze raw meeting transcripts and output a structured summary.

Follow these strict output rules:
1. Tone & Language: Response must be written in professional business Korean.
2. Security (Anonymization): Replace all real names of people with their exact role names (e.g., '김민우 PM' -> 'PM', '이지현 디자이너' -> 'Designer', '최강민 백엔드 리드' -> 'Backend Lead').
3. Strict Fact-based (Anti-Hallucination): Do not assume or invent dates, responsibilities, or tasks that are not explicitly agreed upon in the text.
4. Structuring: Use the following markdown structure for your final response:
   ### 1. 회의 개요
   ### 2. 핵심 의사결정 사항
   ### 3. Action Items (형식: [작업 명칭] - 담당: [역할명] | 기한: [날짜/기한])
   ### 4. 미결 이슈 및 추가 확인 필요
5. Internal Reasoning (Step-by-step): You must perform internal step-by-step reasoning within an XML-style `<thought>` block before generating the final output. Do NOT expose this `<thought>` block to the user in your final output; only output the markdown starting from '### 1. 회의 개요'.
```

---

## 4. Few-shot 예시 (Few-shot Demonstrations)

최소 3개의 예시를 시스템에 주입하여 출력의 일관성을 제어합니다.

### Few-shot 예시 1: 일반적인 성공 케이스
- **Input**:
  "박민수 개발자: 결제창 수정 작업은 제가 담당해서 이번 주 수요일까지 끝내겠습니다."
- **Output**:
  ### 3. Action Items
  - [결제 페이지 UI 수정 및 프론트 개발] - 담당: 개발자 | 기한: 이번 주 수요일

### Few-shot 예시 2: 수치가 혼재된 의사결정 케이스
- **Input**:
  "이영희 마케터: 신규 광고 캠페인 예산을 500만 원으로 가안을 잡았는데, PM님 의견은 어떠신가요? PM: 좋습니다. 500만 원으로 최종 승인합니다."
- **Output**:
  ### 2. 핵심 의사결정 사항
  - 신규 광고 캠페인 최종 예산 500만 원 승인 완료.

### Few-shot 예시 3: 모호한 입력 케이스 (되묻기 유도 규칙)
- **Input**:
  "서대리: 예전에 말씀하신 그 오류 현상, 이번 주 중으로 대충 정리해서 보내드리겠습니다."
- **Output**:
  > [!WARNING]
  > **[시스템 확인 요청]** 제공해주신 회의록 내용이 다소 모호하여 정합성 있는 요약이 어렵습니다. 아래 사항에 대해 보완해 주시면 더욱 정교하게 정리해 드릴 수 있습니다:
  > 1. **오류 현상의 구체적 정의**: "그 오류 현상"이 구체적으로 어떤 모듈/이슈(예: 결제 오류, 로그인 실패 등)인지 확인이 필요합니다.
  > 2. **담당자 명확화**: "서대리"의 정확한 업무 역할명(예: QA 엔지니어, 프론트엔드 개발자 등)이 무엇인지 명시해 주세요.
  > 3. **기한 구체화**: "이번 주 중"의 명확한 마일스톤 날짜(예: 5월 29일 금요일 등)를 명시해 주시면 감사하겠습니다.

---

## 5. 단계적 추론 유도 적용 및 전/후 비교 (Reasoning Prompt Evolution)

### 5.1. v1: 일반 지시 프롬프트 (Naive Prompt)
> "회의록을 읽고 결정사항과 할 일을 정리해 줘."
- **v1 결과 문제점**: 
  - AI가 단계적 추론 과정 없이 즉시 답변을 쓰기 때문에, 문맥이 복잡할 때 담당자와 날짜 매칭 오류가 발생함.
  - 제공되지 않은 정보(예: 기한이 없는 할 일)에 대해 "이번 주 금요일까지" 같은 가상의 날짜를 생성해 내는 환각(Hallucination)이 빈번하게 발생.

### 5.2. v2: 단계적 추론 유도 프롬프트 (Reasoning & Controlled Prompt)
- **개선 사유**: 의사결정과 액션 아이템 매칭의 정확도를 보장하고, 내부 생각 프로세스를 사용자로부터 격리하여 보고서의 가독성을 높이기 위함.
- **추가된 구조적 지시 (Chain of Thought + Encapsulation)**:
  ```text
  - [Phase 1: Fact Extraction] 원시 대화에서 각 발화자의 주장과 약속한 일정을 1대1로 추출한다.
  - [Phase 2: Entity Masking & Security] 추출된 인물들의 이름을 소속 직무/역할명으로 매핑한다.
  - [Phase 3: Hallucination Filtering] 명시적 약속 기한이 없는 항목은 '미결 이슈 및 추가 확인 필요' 섹션으로 강제 격리한다.
  - [Phase 4: Output Synthesis] 오직 최종 markdown 결과물만 노출하고 `<thought>` 블록은 숨긴다.
  ```

---

## 6. 환각(Hallucination) 검증 설계

본 시스템의 환각 검증 메커니즘을 구체적으로 테스트하기 위한 5대 검증 셋과 Pass/Fail 기준입니다.

### 6.1. Pass/Fail 판정 규칙 (Evaluation Rules)
- **Pass (합격)**:
  - **(A) 정확한 매칭**: 원문의 팩트와 마일스톤 기한이 정확히 매치되고 근거를 함께 제시함.
  - **(B) 모름/확인 필요 명시**: 원문에 정보가 없거나 모호하면 자의적으로 지어내지 않고, "원문에 명시되지 않음. 추가 확인 필요"라고 명확히 공지하고 확인 절차를 제안함.
- **Fail (불합격)**:
  - 잘못된 정보나 날짜를 단정적으로 답함.
  - 질문 전제가 누락되었음에도 확인 질문 없이 임의로 날짜나 담당자를 선언함.

### 6.2. 5대 사실 기반 검증 질문 셋 (5 Verification QA Sets)

| 번호 | 검증 질문 (Verification Question) | 기대 정답 및 판정 근거 (Expected Answer & Rationale) | 판정 결과 (Pass/Fail) |
| :---: | :--- | :--- | :---: |
| **Q1** | 디자인 시안을 퍼블리싱 담당자에게 전달하기로 합의된 최종 기한은 언제인가요? | 이번 주 금요일 (이지현 디자이너 발언에 기반함) | **Pass (A)** |
| **Q2** | A/B Testing 인프라 사전 검증의 담당자와 마일스톤 기한은 누구이며 언제인가요? | 담당: 프론트 개발자 (실명 박태양 배제) / 기한: 다음 주 화요일 | **Pass (A)** |
| **Q3** | 백엔드 팀 연동 이슈는 누가 누구에게 조율을 요청하기로 최종 결정되었나요? | PM이 백엔드 리드에게 조율을 요청하기로 함. (실명 김민우, 최강민 배제 검증) | **Pass (A)** |
| **Q4** | 프론트엔드 개발 착수 예정일은 언제로 합의되었나요? | 다음 주 월요일 (PM의 최종 조율 발언에 근거함) | **Pass (A)** |
| **Q5** | 이번 회의에서 모바일 앱 스토어 심사 등록을 6월 15일까지 완료하기로 최종 합의했나요? | **"원문에 해당 내용이 존재하지 않으며 최종 합의되지 않음"**이라고 선언하고 추가 확인이 필요하다고 안내해야 함. | **Pass (B)** |
