# [Project B] 뉴스 요약 자동화 워크플로우 만들기

본 프로젝트는 노코드 자동화 툴(Make.com)과 생성형 AI(OpenAI)를 활용하여 외부 RSS 피드로부터 최신 IT/AI 기술 뉴스를 자동으로 수집하고, 핵심 내용을 요약하여 Notion 데이터베이스에 체계적으로 저장하는 **뉴스 수집 및 요약 자동화 파이프라인** 프로젝트입니다.

---

## 1. 프로젝트 요약 (Project Summary)

- **목적**: 수동으로 매번 여러 IT 사이트와 블로그를 탐색하여 조사하는 번거로움을 해결하고, 최신 기술 뉴스를 매일 아침 자동으로 분석·축적하여 비즈니스/기술 리서치 리소스를 최적화합니다.
- **핵심 흐름**:
  1. **Trigger**: 매일 오전 09:00 (KST) 자동으로 실행되는 스케줄러 트리거 작동.
  2. **Data Collection (RSS)**: 지정된 RSS 피드(Hacker News 등)로부터 최신 기사 정보 수집.
  3. **Filtering**: 수집된 기사 중 사전에 정의된 AI/IT 관련 핵심 키워드가 포함된 기사 1건 선별.
  4. **AI Processing**: OpenAI GPT 모델을 호출하여 뉴스 요약을 3줄의 글머리 기호 형태로 작성.
  5. **Auto Save**: Notion 데이터베이스에 제목, 요약문, 원문 링크, 발행일시를 중복 없이 저장.
- **안정성 및 운영 정책**:
  - **중복 방지**: 원문 URL을 Key값으로 활용하여 동일 기사의 중복 저장 원천 방지.
  - **에러 핸들링**: OpenAI 및 Notion API 호출 오류 시 최대 2회 자동 재시도(Retry) 후, 지속적인 실패 시 무시(Ignore)하여 파이프라인 정지나 과금 폭탄 방지.

---

## 2. 폴더 구조 (Folder Structure)

Project-B의 전체 폴더 구조와 각 파일의 명세는 다음과 같습니다.

```text
Project-B/
├── README.md                     # 프로젝트 종합 안내 문서 (본 문서)
├── mission-details.md            # [Project B] 마스터 과제 설명 및 요구사항 문서
├── required_mission.md           # 필수 요구사항 분석 및 산출물 체크리스트
├── workflow_architecture.md      # 스케줄 기반 RSS-AI-Notion 파이프라인 아키텍처 및 설정 가이드 (Mermaid 포함)
└── notion_db_schema.md           # 결과를 저장할 Notion 데이터베이스 속성(Properties) 세팅 명세서
```

### 파일별 세부 역할 (File Details)

- **[mission-details.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-B/mission-details.md)**
  - 본 프로젝트의 배경, 요구 조건, 보너스 미션(썸네일 생성, 감성 분석 등) 및 제약 사항이 기록된 원본 과제 상세 정보 문서입니다.
- **[required_mission.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-B/required_mission.md)**
  - 데이터 수집, AI 가공, 자동 저장 및 안정성 확보 등 필수 구현 요구사항을 분석하고 정리한 산출물 요구 정의서입니다.
- **[workflow_architecture.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-B/workflow_architecture.md)**
  - Make.com 등의 툴을 활용하여 파이프라인을 구축할 때 필요한 모듈별(Trigger, RSS, OpenAI, Notion, Error Handler) 상세 설정 가이드와 Mermaid 아키텍처 다이어그램 문서입니다.
- **[notion_db_schema.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-B/notion_db_schema.md)**
  - 요약된 뉴스 데이터를 안정적이고 가독성 있게 보관하기 위한 Notion 데이터베이스 속성(컬럼명 및 컬럼 타입) 정의서입니다.
