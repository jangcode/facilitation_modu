# [Project A] AI 기반 UI/UX 디자인 시안 제작

본 프로젝트는 AI 기반 UI/UX 디자인 특화 도구인 **Stitch**를 활용하여 여행 및 숙박 예약 모바일 앱의 핵심 화면을 생성하고, 이를 실제 작동하는 흐름으로 연결하는 **인터랙티브 프로토타입 시안 제작** 프로젝트입니다.

---

## 1. 프로젝트 요약 (Project Summary)

- **목적**: 텍스트 프롬프트 작성을 통한 UI/UX 아이디어의 고속 시각화 및 프로토타입 구체화 역량을 확보합니다.
- **핵심 흐름**:
  1. **Prompt Engineering**: UI/UX에 최적화된 프롬프트를 점진적으로 수정하며 메인/검색(Home), 검색 결과(Search Results), 상세(Detail) 화면을 생성.
  2. **Image Generation & Post-Processing**: Stitch 도구를 활용하여 화면 스타일 일관성을 유지하고, 텍스트 깨짐 현상을 직접 덮어쓰기(Edit/Text Overlay)로 후가공 및 보정.
  3. **Prototyping**: Stitch의 클릭 영역(Hotspot) 연결 기능을 사용하여 Home ➡️ Search Results ➡️ Detail 화면으로 이어지는 실제 이동 흐름 및 뒤로 가기(Back) 인터랙션을 정의.
- **핵심 성과**: AI 기반 생성 도구를 실무 UI/UX 시각화 및 기획 초기 프로토타이핑 워크플로우에 성공적으로 이식하여 비주얼 커뮤니케이션을 극대화함.

---

## 2. 폴더 구조 (Folder Structure)

Project-A의 전체 폴더 구조와 각 파일의 명세는 다음과 같습니다.

```text
Project-A/
├── README.md                      # 프로젝트 종합 안내 문서 (본 문서)
├── mission-details.md             # [Project A] 마스터 과제 설명 및 요구사항 문서
├── required_mission.md            # 필수 요구사항 정의 및 산출물 체크리스트
├── Stitch_프로토타입_가이드.md     # Stitch 툴을 이용한 UI 수정 및 화면 연동 프로토타입 가이드북
├── 작업 로그.md                  # 사용한 프롬프트의 개선 과정(초안→수정→최종) 기록 문서
├── stitch_home_screen.png         # Stitch 내 생성된 홈 화면 시안 (Figma/Editor 배치용)
├── stitch_results_screen.png      # Stitch 내 생성된 검색 결과 화면 시안
├── stitch_detail_screen.png       # Stitch 내 생성된 호텔 상세 화면 시안
├── travel_home_screen.png         # 텍스트 깨짐 및 레이아웃이 보정된 여행 앱 홈 최종 시안
├── travel_results_screen.png      # 보정된 검색 결과 최종 시안
└── travel_detail_screen.png       # 보정된 호텔 예약 상세 최종 시안
```

### 파일별 세부 역할 (File Details)

- **[mission-details.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-A/mission-details.md)**
  - UI 디자인 이미지 규격, 피그마 연동 요구사항, 프롬프트 로그 가이드 등 과제의 전체적인 개요와 채점 기준을 포함한 마스터 문서입니다.
- **[required_mission.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-A/required_mission.md)**
  - 이미지 생성, 프롬프트 기록, 후가공, 프로토타이핑에 이르는 핵심 요구 조건을 체계적으로 매핑하고 관리하는 과제 기획/요구 분석서입니다.
- **[Stitch_프로토타입_가이드.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-A/Stitch_%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85_%EA%B0%80%EC%9D%B4%EB%93%9C.md)**
  - Stitch 프로젝트 ID(`15566429067796604140`)를 기반으로 툴에 접속하여 텍스트를 후가공하고 화면 간 이동 경로(Hotspot)를 연결하는 실무 실행 지침서입니다.
- **[작업 로그.md](file:///d:/03-Biz/codyssey-project/native-basic/Project-A/%EC%9E%91%EC%97%85%20%EB%A1%9C%EA%B7%B8.md)**
  - 3개 화면(홈, 검색 결과, 상세)의 이미지 생성을 위해 사용된 프롬프트들이 어떻게 고도화되었는지에 대한 로그와 수정 사유를 담은 일지입니다.
- ***.png (시안 이미지 파일들)**
  - `stitch_*.png`는 AI 특화 도구 Stitch에서 일차적으로 생성된 모바일 레이아웃 시안 이미지입니다.
  - `travel_*.png`는 텍스트 뭉개짐이나 구도 결함을 보정하고, 핫스팟 연동 및 실제 모바일 화면에 가깝게 가공을 마친 최종 프로토타입 이미지 리소스입니다.
