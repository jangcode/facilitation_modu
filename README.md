# B1-1 미션 패키지: LLM 기반 업무 자동화 (회의록 요약)

본 저장소는 대규모 언어 모델(LLM)을 업무에 투입하여 정량적으로 성능을 비교하고, 시스템 프롬프트 및 페르소나 설계를 통해 회의록 요약 과업을 안전하고 정확하게 자동화한 산출물 패키지입니다.

---

## 1. 폴더 구조 및 구성 파일 설명

```text
d:\03-Biz\codyssey-project\native-basic\B1-1\
│
├── README.md                     # 본 문서 (과제 수행 절차 및 파일 소개)
├── mission-detailes.md           # 미션 요구사항 원본 문서
├── 회의록.md                     # 실습용 원본 회의록 (수입 주류 마그네틱 씰 협의 건)
│
├── required_mission.md           # 미션 심층 분석 및 요구사항 정의서
├── model_comparison_report.md    # 3종 LLM 성능 비교 및 모델 선정 보고서
├── system_design.md              # 페르소나, 시스템 프롬프트, Few-shot 및 검증 설계서
├── execution_log.md              # 10턴 대화 시나리오 및 조건 변경 실행 로그
└── goal_report.md                # 확률적 생성, 환각 원인 및 프롬프트 기법 분석 보고서
```

- **[required_mission.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-1/required_mission.md)**: 미션 요구사항을 기능/비기능으로 나누고 산출물 작업 목록을 구체화한 분석서입니다.
- **[model_comparison_report.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-1/model_comparison_report.md)**: GPT-5.5 Instant, Claude 4.6 Sonnet, Gemini 3.5 Flash 모델을 4가지 정량 평가 축을 기준으로 벤치마킹하여 최종 모델(Claude 4.6 Sonnet)을 선정한 비교서입니다.
- **[system_design.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-1/system_design.md)**: 비즈니스 도메인에 특화된 정훈 PM 페르소나와 실명 익명화 필터, 환각 방지용 Few-shot 및 단계적 추론(Reasoning) 기법이 결합된 시스템 프롬프트 설계서입니다.
- **[execution_log.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-1/execution_log.md)**: 실제 챗봇과의 10턴 이상 대화 과정을 기록하였으며, 중간 대화 톤앤매너 변경, 역할 명칭 변경 지시 및 기한 정보의 추가 유입 등 동적 컨텍스트가 완벽하게 유지됨을 검증한 대화록입니다.
- **[goal_report.md](file:///d:/03-Biz/codyssey-project/native-basic/B1-1/goal_report.md)**: LLM의 통계적 예측 및 생성에 따른 환각 발생 원인을 설명하고, Zero/Few-shot 및 Reasoning 프롬프트를 적재적소에 활용하기 위한 기술 분석 리포트입니다.

---

## 2. 과제 수행 절차 요약

1. **요구사항 분석 및 구체화 (`required_mission.md` 작성)**
   - 미션 원본 문서를 바탕으로 평가자가 요구하는 동료 평가 기준과 필수 산출물을 누락 없이 나열하고 매뉴얼화하였습니다.
2. **LLM 벤치마크 테스트 (`model_comparison_report.md` 작성)**
   - 동일한 과업 입력 데이터를 3종 모델에 투입하여 정확성, 한국어 품질, 형식 준수, 문맥 유지력을 정량 비교하였습니다.
3. **업무용 시스템 프롬프트 및 필터링 설계 (`system_design.md` 작성)**
   - 회의록 내의 개인 실명을 감추기 위해 역할명 마스킹 규칙을 도입하였고, 모호한 정보가 입력되었을 경우 모델이 자의적으로 추정하여 환각을 일으키는 대신 사용자에게 최대 3개의 질문을 반환하도록 Few-shot 설계를 완료했습니다.
4. **실행 테스트 및 문맥 연속성 검증 (`execution_log.md` 작성)**
   - 정훈 페르소나 봇과의 실질적인 10턴 대화를 시뮬레이션하여 톤 전환과 정보 갱신(기한 추가 등)이 컨텍스트 내에서 흐트러짐 없이 유지됨을 증명하였습니다.
5. **학습 성과 리포트 작성 (`goal_report.md` 작성)**
   - 과제 목표를 관통하는 LLM 핵심 원리 및 프롬프트 개선 루프의 의의를 기술적으로 완결성 있게 해설하고 축적하였습니다.
