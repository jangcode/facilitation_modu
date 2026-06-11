# Notion 데이터베이스 스키마 설계

결과물을 저장할 Notion 데이터베이스의 구조(속성/컬럼)와 뷰(View) 설계안입니다. 하나의 DB에 모든 플랫폼 결과를 저장하되, '플랫폼' 태그로 필터링하여 관리합니다.

## 1. 데이터베이스 속성(Properties)

| 속성명(Property) | 타입(Type) | 설명(Description) |
| :--- | :--- | :--- |
| **제목(Title)** | Title | 콘텐츠의 메인 주제 (예: 2025년 AI 트렌드) |
| **플랫폼(Platform)** | Select | Instagram, Blog, X(Twitter) 중 하나 선택 |
| **톤앤매너(Tone)** | Select | (A/B 테스트용) Professional, Friendly 중 하나 |
| **생성 텍스트(Content)** | Text | AI가 생성한 결과 텍스트 (줄바꿈 및 포맷팅 포함) |
| **이미지(Image URL)** | URL | DALL-E 3가 생성한 이미지의 웹 링크 |
| **작업 상태(Status)** | Status | `To Do` (초안 생성됨), `In Progress` (검토중), `Done` (업로드 완료) |
| **생성 일시(Created At)** | Created Time | 데이터가 자동 추가된 시각 |

## 2. 권장하는 보기(Views) 구조

Notion DB 상단 탭에 다음 View들을 추가하여 관리 효율을 높입니다.

1. **전체 보기 (All)**: Table View - 모든 컬럼과 모든 행을 시간순으로 정렬하여 봅니다.
2. **보드 보기 (Kanban Board)**: Board View - `작업 상태(Status)` 기준으로 그룹화하여, 초안 -> 검토 -> 업로드 완료의 진행 과정을 드래그앤드롭으로 관리합니다.
3. **인스타그램 뷰 (Instagram Only)**: Gallery View - `플랫폼`이 `Instagram`인 것만 필터링하고, 카드 커버를 `이미지(Image URL)`로 설정하여 피드 느낌을 미리 봅니다.
4. **블로그 뷰 (Blog Only)**: List View - `플랫폼`이 `Blog`인 것만 필터링하여, 텍스트 중심으로 리뷰합니다.
