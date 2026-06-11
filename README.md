# 미션 3: 노코드 자동화 기초 - 워크플로우 설계

이 디렉토리는 반복적인 비즈니스 업무를 발굴하고, 이를 노코드 툴(Make, Zapier)을 사용하여 자동화하는 미션의 수행 결과물과 분석 보고서를 포함하고 있습니다.

---

## 1. 과제 수행 절차 및 내용

1. **요구사항 분석**: `mission-details.md`와 `native_check_list.md`를 바탕으로 필수 요구조건 및 제약조건을 도출하여 `required_mission.md` 작성.
2. **도구 비교 설계 [프로젝트 1]**: Google Forms 만족도 설문 접수 시 점수를 검사하여 Google Sheets 기록 및 Slack 채널 알림을 전송하는 동일 워크플로우를 Make와 Zapier로 각각 구축 및 상세 비교 분석 보고서(`compare_report.md`) 작성.
3. **자유 주제 설계 [프로젝트 2]**: Notion 데이터베이스에 새 회의록이 생성되었을 때 생성형 AI API(OpenAI/Gemini)로 핵심 요약 및 카테고리를 자동 분류하고 적합한 Slack 채널로 알림을 라우팅하며, 에러 발생 시 이메일로 실패 알림을 발송하는 안정적인 자동화 시나리오(`custom_automation.md`) 설계.
4. **학습 성과 정리**: 자동화의 기본 요소(Trigger, Action, Filter, Router)를 정립하고 학습 성과를 기술한 `goal_report.md` 작성.

---

## 2. 폴더 구조 및 산출물 설명

```directory
B1-3/
│
├── mission-details.md       # 미션 원본 가이드라인 문서
├── required_mission.md      # 미션 요구사항 정의서
├── compare_report.md        # [프로젝트 1] Make vs Zapier 비교 분석 보고서
├── custom_automation.md     # [프로젝트 2] Notion + AI 요약 + Slack 알림 자동화 설계서
├── goal_report.md           # 미션 핵심 개념 정리 및 최종 학습 결과 보고서
└── README.md                # 전체 미션 수행 설명서 (본 파일)
```

- [required_mission.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-3/required_mission.md): 기능/비기능 요구사항 분석 및 산출물 체크리스트.
- [compare_report.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-3/compare_report.md): 동일 시나리오 하에서 Make와 Zapier의 실행 과정, 로그 비교, 5대 평가 항목 테이블.
- [custom_automation.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-3/custom_automation.md): Notion 데이터베이스 감지 트리거, LLM 기반 요약 및 분류 액션, Slack 라우팅 및 예외 발생 시 Gmail 전송 에러 핸들링 설계.
- [goal_report.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-3/goal_report.md): Trigger/Action/Router 개념 정의 및 업무 적합성 판단 근거 정리.
