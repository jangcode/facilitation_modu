# [Project C] AI 기반 소셜 미디어 콘텐츠 자동 생성

본 프로젝트는 하나의 주제나 키워드를 입력받았을 때, 다양한 소셜 미디어 플랫폼(Instagram, Blog, X)의 포맷과 특성에 맞는 콘텐츠(텍스트 및 이미지)를 자동으로 생성하고, 이를 Notion 데이터베이스에 자동으로 축적하는 **콘텐츠 제작 파이프라인 자동화 워크플로우** 설계 및 기획 프로젝트입니다.

---

## 1. 프로젝트 요약 (Project Summary)

- **목적**: 소셜 미디어 마케팅 시 여러 플랫폼에 맞춰 콘텐츠를 매번 재가공하는 반복적인 수작업을 자동화하여 생산성을 극대화합니다.
- **핵심 흐름**:
  1. **Trigger**: Slack 채널에 명령어 입력 (예: `!콘텐츠생성 [주제]`)
  2. **AI Generation**: 
     - **OpenAI GPT-4o**: 인스타그램(짧은 캡션+이모지+해시태그), 블로그(장문+소제목 구조), X(200자 이내 3줄 요약) 맞춤형 텍스트 생성
     - **OpenAI DALL-E 3**: 주제를 시각화한 블로그/소셜 미디어용 대표 이미지 생성
  3. **Action (Notion DB)**: 플랫폼별 속성(Properties)과 태그를 기반으로 하나의 Notion 데이터베이스에 자동 저장 및 상태 관리
  4. **Notification**: 작업이 완료되면 Slack 스레드 답변을 통해 Notion 링크 알림
- **추가 기능 (A/B Test)**: 동일 주제에 대해 전문적인 톤(Professional)과 친근한 톤(Friendly)으로 텍스트를 나누어 생성하는 A/B 테스트 전략 수립

---

## 2. 폴더 구조 (Folder Structure)

Project-C의 전체 폴더 구조와 각 파일의 명세는 다음과 같습니다.

```text
Project-C/
├── README.md                     # 프로젝트 종합 안내 문서 (본 문서)
├── mission-details.md            # [Project C] 마스터 과제 설명 및 요구사항 문서
├── required_mission.md           # 필수 요구사항 분석 및 산출물 체크리스트
├── workflow_architecture.md      # Slack-OpenAI-Notion 아키텍처 및 파이프라인 설계도 (Mermaid 포함)
├── prompt_templates.md           # 플랫폼별 GPT-4o 시스템 프롬프트 및 DALL-E 3 프롬프트 변환기 템플릿
├── notion_database_schema.md     # 결과 저장용 Notion DB 속성(Properties) 및 View 구성 설계안
├── ab_test_scenario.md           # 톤앤매너 분기 및 효과 측정을 위한 A/B 테스트 시나리오 기획서
└── sample_outputs.md             # '2025년 AI 트렌드와 직업의 변화' 주제의 가상 실행 결과물 예시
```

### 파일별 세부 역할 (File Details)

- **[mission-details.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/mission-details.md)**
  - 본 미션의 기획 배경, 최종 산출물 규격, 상세 기능 요구사항 및 보너스 과제 등의 제약 조건을 기술한 마스터 문서입니다.
- **[required_mission.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/required_mission.md)**
  - 최종 완성을 위해 수행해야 할 기능 요구사항과 산출물 목록을 한눈에 볼 수 있도록 요약 정리한 체크리스트입니다.
- **[workflow_architecture.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/workflow_architecture.md)**
  - Slack에서 입력받아 Notion으로 저장되기까지의 데이터 흐름을 Mermaid 다이어그램 및 모듈별 역할 정의로 시각화한 아키텍처 설계 문서입니다.
- **[prompt_templates.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/prompt_templates.md)**
  - 각 플랫폼의 고유 특성(글자 수 제한, 이모지 유무, 소제목 여부 등)을 극대화하기 위해 설계된 System Prompt 모음입니다.
- **[notion_database_schema.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/notion_database_schema.md)**
  - Notion 테이블의 스키마 구조(Title, Select, URL, Status 등) 및 칸반보드/갤러리 보기와 같은 맞춤형 뷰(View) 설계안입니다.
- **[ab_test_scenario.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/ab_test_scenario.md)**
  - 전문적이고 신뢰감 있는 톤(Professional)과 친근하고 트렌디한 톤(Friendly)의 자동 분기 및 성과 지표(Metrics) 측정을 위한 시나리오 가이드라인입니다.
- **[sample_outputs.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-C/sample_outputs.md)**
  - 설계된 프롬프트 템플릿과 워크플로우를 거쳐 실제로 도출되는 최종 텍스트와 이미지 정보의 구체적인 결과 예시입니다.
