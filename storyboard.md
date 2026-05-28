# NeoSeoul 브랜드 광고 스토리보드 (Storyboard)

이 문서는 AI 기반 멀티모달 콘텐츠 제작 파이프라인을 활용하여 기획한 **NeoSeoul** 스트릿 브랜드의 티저 광고 스토리보드입니다.

---

## 1. 브랜드 및 캠페인 정의

### 브랜드 아이덴티티 (Brand Identity)
* **브랜드명**: NeoSeoul (네오서울)
* **타겟**: 10~20대 트렌디하고 개성 강한 스트릿 패션 매니아층
* **톤앤매너**: 사이버펑크(Cyberpunk), 네온(Neon), 비 내리는 서울 밤거리, 시네마틱(Cinematic), 테크웨어(Techwear) 스타일
* **핵심 가치 및 차별점 (USP)**: 
  * "서울 고유의 전통적/현대적 감성과 미래적 사이버 테크웨어 실루엣의 융합"
  * 한정판 수량으로만 발매되는 드롭(Drop) 시스템 기반의 희소성 확보
* **핵심 메시지 (One-Line Campaign Message)**: 
  > **“오늘 밤, 너의 서울을 입어라.” (Tonight, wear your Seoul.)**

### 광고 캠페인 개요
* **광고 목적**: 신규 시즌 테크웨어 라인업 런칭 티저 및 브랜드 인지도 제고 (Brand Awareness)
* **총 영상 길이**: 37초
* **주요 타겟 미디어**: 유튜브 쇼츠 및 인스타그램 릴스/피드

---

## 2. 도구 활용 및 제약 사항 대비 계획

### 활용 생성형 AI 도구 목록
1. **텍스트 & 컨셉 기획**: Google Gemini 1.5 Pro & Gemini 2.0 (스토리보드 기획 및 프롬프트 고도화)
2. **이미지 생성**: Google Imagen 3 (고화질 사이버펑크 키 비주얼 생성)
3. **비디오 변환**: Google Veo & Runway Gen-3 (정지 이미지를 시네마틱 모션 컷으로 변환)
4. **오디오 생성**: Suno AI & Google MusicLM (사이버펑크 비트와 도시 환경음 합성)

### 도구 접근성 및 리소스 제약 대비 계획
* **이미지 생성 대안**: Imagen 3 장애 또는 크레딧 부족 시 -> Midjourney v6 또는 Stable Diffusion XL 사용
* **비디오 생성 대안**: Google Veo/Runway 대기열 지연 시 -> Luma Dream Machine 또는 Kling AI 사용
* **오디오 생성 대안**: Suno AI 크레딧 소모 시 -> Udio 또는 ElevenLabs(내레이션 전용) 사용
* **크레딧 절약 전략**:
  * 씬 구성을 5개로 정예화하여 불필요한 비디오 생성 리소스를 최소화함.
  * Imagen 3에서 스타일 가이드를 명확히 지정해 스타일의 일관성을 확보한 뒤, 통과된 에셋만 비디오 변환을 수행함.

---

## 3. 씬별 세부 스토리보드 (Scenes Detail)

### 씬 1 : 인트로 (Intro)
* **씬 번호 / 씬 길이**: Scene #1 / 6초
* **목표 메시지**: 브랜드의 세계관(서울-네온-비)을 한 컷에 깊이 각인시킨다.
* **화면 구성**:
  * **구도**: 광각 로우 앵글 (Wide Low-angle)
  * **피사체 & 배경**: 젖어 있는 아스팔트 도로 위로 화려한 핑크와 시안(Cyan) 빛 네온사인이 반사된다. 그 너머로 어두운 실루엣의 테크웨어 후드를 쓴 인물이 서서히 카메라를 등지고 서 있다.
  * **텍스트**: 화면 중앙에 얇은 폰트로 "NEOSEOUL" 로고가 서서히 타이핑 효과로 등장.
* **내레이션 (Voiceover)**: "서울의 밤은... 늘 새롭게 다시 태어난다." (낮고 시네마틱한 보이스)
* **사용 도구 및 목적**:
  * 이미지 생성: **Imagen 3** (비 내리는 네온 서울 골목과 인물 실루엣의 미장센 확보)
  * 비디오 변환: **Runway Gen-3** (네온사인의 미세한 깜빡임과 빗방울이 바닥에 튀는 모션 연출)
  * 오디오 생성: **Suno AI** (비 내리는 빗소리 환경음이 가미된 차분하고 신비로운 사이버펑크 로파이 비트)
* **입력 프롬프트**:
  ```text
  Cinematic wide low-angle shot, wet asphalt street of Seoul at night, hyper-detailed neon signs in cyan and magenta colors reflecting on puddle, dark silhouette of a person wearing a futuristic techwear hoodie with back to the camera, gentle rain falling, cyberpunk style, photorealistic, 8k, Unreal Engine 5 render feel, moody atmosphere.
  ```
* **출력 결과 요약**: 빗방울과 네온 반사광이 역동적으로 어우러지는 도시 실루엣 비주얼 완성.
* **결과 파일명**: `scene01_intro_keyvisual.png` / `scene01_intro_motion.mp4` / `scene01_intro_ambient.wav`

---

### 씬 2 : 디테일 포커스 (Brand Identity Detail)
* **씬 번호 / 씬 길이**: Scene #2 / 8초
* **목표 메시지**: 테크웨어 자켓의 미래지향적 광섬유 패턴과 의상 텍스처를 극대화하여 제품의 USP를 보여준다.
* **화면 구성**:
  * **구도**: 익스트림 클로즈업 (Extreme Close-up)
  * **피사체 & 배경**: 테크웨어 자켓의 지퍼와 고밀도 나일론 방수 소재 텍스처. 지퍼 라인을 따라 흐르는 광섬유(Optical Fiber) 라인이 파란색에서 보라색으로 그라데이션되며 빛을 발한다.
  * **텍스트**: 없음.
* **내레이션 (Voiceover)**: "빛으로 새겨진 실루엣, 테크놀로지가 스타일이 되는 순간."
* **사용 도구 및 목적**:
  * 이미지 생성: **Imagen 3** (광섬유가 삽입된 고기능성 의류의 디테일과 질감 묘사)
  * 비디오 변환: **Google Veo** (자켓 지퍼 주위의 미세한 카메라 틸트업과 광섬유 라인을 따라 흐르는 네온 빛의 움직임 연출)
  * 오디오 생성: **Google MusicLM** (기계적이고 하이테크한 분위기를 내는 신디사이저 아르페지오 사운드)
* **입력 프롬프트 (수정 후 최종)**:
  ```text
  Extreme close-up shot of a futuristic cyberpunk techwear jacket zipper, hyper-detailed waterproof dark tech-nylon fabric texture, glowing optical fiber glowing tubes integrated into seams shifting color from electric blue to violet, soft neon ambient lighting, volumetric fog, cinematic macro photography, 8k, flawless detailing.
  ```
* **출력 결과 요약**: 섬세한 직물 짜임새와 몽환적인 광섬유 발광이 살아있는 매크로 영상 확보.
* **결과 파일명**: `scene02_detail_keyvisual.png` / `scene02_detail_motion.mp4` / `scene02_synth_arpeggio.wav`

> [!IMPORTANT]
> **씬 2 프롬프트 개선 로그 (Prompt Improvement Log)**
> * **수정 전 프롬프트**: `cyberpunk jacket close-up, glowing blue lights, detailed clothing`
> * **문제점**: 직물의 정교함이 부족해 일반 패션 광고처럼 보이지 않았고, 발광 부위가 부자연스러운 덩어리로 뭉쳐 공상과학 영화의 저렴한 소품처럼 묘사됨. 톤앤매너 일관성이 훼손됨.
> * **수정 사유 및 조치**: 
>   * 패브릭의 사실적 묘사를 위해 질감 명시(`waterproof dark tech-nylon fabric texture`, `extreme close-up`)를 추가함.
>   * 촌스러운 불빛을 세련된 미래주의 디자인으로 변경하기 위해 `glowing optical fiber glowing tubes integrated into seams shifting color from electric blue to violet`와 같이 세부 발광 방식 및 그라데이션 컬러를 구체적으로 한정함.
> * **수정 후 결과**: 자켓 재봉선을 따라 미세한 광섬유 튜브가 흐르는 고급스러운 테크웨어 질감이 극대화되어 세련된 브랜드 USP가 확연히 부각됨.

---

### 씬 3 : 도시의 질주 (Street Action)
* **씬 번호 / 씬 길이**: Scene #3 / 8초
* **목표 메시지**: 역동적인 테크웨어 브랜드의 활동성과 스트릿 무드를 강렬하게 전개한다.
* **화면 구성**:
  * **구도**: 사이드 패닝 트래킹 샷 (Side-panning Tracking Shot)
  * **피사체 & 배경**: 헬멧을 쓴 모델이 광원 잔상이 흐르는 어두운 밤거리를 미래형 전기 모터사이클을 타고 질주한다. 모델이 입은 네오서울 바람막이가 바람에 흩날린다.
  * **텍스트**: 화면 구석에 빠르게 지나가는 홀로그램 좌표 텍스트.
* **내레이션 (Voiceover)**: "속도가 지배하는 도시의 거리를 가로질러."
* **사용 도구 및 목적**:
  * 이미지 생성: **Imagen 3** (전기 바이크의 미래형 기하학적 디자인과 바람막이의 모션 레퍼런스 확보)
  * 비디오 변환: **Runway Gen-3** (바이크의 바퀴 회전, 흩날리는 옷자락, 뒤로 빠르게 지나가는 도시 가로등의 모션 블러를 역동적으로 구현)
  * 오디오 생성: **Suno AI** (급박하게 몰아치는 일렉트로닉 드럼 앤 베이스 비트와 날카로운 바이크 모터 사운드 이펙트)
* **입력 프롬프트**:
  ```text
  Side-view tracking shot, futuristic electric motorcycle speeding through a dark rain-soaked cyberpunk city street, rider wearing fully-enclosed matte black helmet and loose oversized techwear windbreaker jacket fluttering in the wind, neon trails blurred in the background, cinematic speed, camera panning dynamically, dramatic neon illumination, photorealistic.
  ```
* **출력 결과 요약**: 바람에 흩날리는 테크웨어 피츠와 스피디한 배경 잔상이 결합된 고속 모션 연출.
* **결과 파일명**: `scene03_action_keyvisual.png` / `scene03_action_motion.mp4` / `scene03_dnb_beat.wav`

---

### 씬 4 : 모델 군상과 슬로건 (Models & Slogan)
* **씬 번호 / 씬 길이**: Scene #4 / 10초
* **목표 메시지**: 다양한 인물이 주는 당당함과 일관된 스타일링을 통해 네오서울만의 독보적 소속감을 전한다.
* **화면 구성**:
  * **구도**: 아이 레벨 쓰리샷 (Eye-level Three-shot)
  * **피사체 & 배경**: 각기 다른 개성을 가진 세 명의 남녀 모델들이 나란히 서서 카메라를 향해 정면으로 강렬한 시선을 보낸다. 씬 1과 씬 2의 화풍 및 색채가 완벽히 이어지며, 몽환적인 홀로그램 네온 사인이 공중에 투영된다.
  * **텍스트**: 화면 하단에 묵직하게 나타나는 핵심 슬로건: "오늘 밤, 너의 서울을 입어라."
* **내레이션 (Voiceover)**: "규칙은 없다. 너만의 스타일로 증명할 뿐."
* **사용 도구 및 목적**:
  * 이미지 생성: **Imagen 3** (다양한 인물의 얼굴 묘사와 함께 옷 스타일, 시안-마젠타 색조 일관성 고정)
  * 비디오 변환: **Google Veo** (모델들의 미세한 호흡, 눈빛 흔들림, 자켓의 미세한 움직임을 풍부하게 표현)
  * 오디오 생성: **Suno AI** (인트로의 로파이 빗소리와 아웃트로의 비트가 자연스럽게 전환되는 무거운 힙합 드럼 비트)
* **입력 프롬프트**:
  ```text
  Eye-level portrait of three diverse fashion models standing shoulder-to-shoulder, intensely staring at the camera, wearing cyberpunk technical streetwear, consistent neon lighting in cyan and magenta, floating holographic Korean text on the side, cinematic smoke, ultra-realistic skin details, masterpiece quality.
  ```
* **출력 결과 요약**: 톤앤매너가 완벽하게 일치하는 세 모델의 카리스마 있는 시선 컷 획득.
* **결과 파일명**: `scene04_group_keyvisual.png` / `scene04_group_motion.mp4` / `scene04_hiphop_beat.wav`

---

### 씬 5 : 아웃트로 (Outro - CTA)
* **씬 번호 / 씬 길이**: Scene #5 / 5초
* **목표 메시지**: 브랜드 로고와 런칭 일정을 각인시키고 공식 채널로의 방문을 유도한다.
* **화면 구성**:
  * **구도**: 정면 평면 구도 (Frontal Graphic Layout)
  * **피사체 & 배경**: 어두운 콘크리트 질감 위에 금속성 재질의 "NEOSEOUL" 3D 엠블럼 로고가 놓여 있다. 로고 외곽선을 따라 붉은빛 레이저가 지나가며 반짝인다.
  * **텍스트**: "2026.06.01 LIMITED DROP" 및 인스타그램 아이디 "@NEOSEOUL_OFFICIAL"
* **내레이션 (Voiceover)**: "NEOSEOUL. 한정 드롭을 만나보세요."
* **사용 도구 및 목적**:
  * 이미지 생성: **Imagen 3** (금속적이고 입체적인 브랜드 로고 엠블럼 디자인 제작)
  * 비디오 변환: **Runway Gen-3** (엠블럼에 비치는 메탈릭 릭 플레어와 빛 번짐, 레이저 스캔 효과 모션 부여)
  * 오디오 생성: **Suno AI** (임팩트 있고 묵직한 베이스 드롭 사운드로 여운을 주는 아웃트로 종결음)
* **입력 프롬프트**:
  ```text
  3D metallic emblem logo design of 'NEOSEOUL', dark minimalist concrete background, red laser scanner beam sweeping across the sharp edges of the logo, cinematic lighting, sharp reflections, premium look, clean graphics.
  ```
* **출력 결과 요약**: 강렬한 브랜드 메탈릭 로고 컷 및 마케팅 CTA 정보 각인.
* **결과 파일명**: `scene05_outro_keyvisual.png` / `scene05_outro_motion.mp4` / `scene05_bass_drop.wav`

---

## 4. 스타일 일관성 제어 및 에셋 네이밍 규칙

### 스타일 및 일관성 제어 전략 (Consistency Control)
1. **Style Reference (sref) 활용**: 모든 이미지 생성 시, 사이버펑크 톤앤매너(시안/마젠타 대비, 젖은 질감, 시네마틱 라이팅)를 공통으로 묘사하는 기준 이미지 `scene01_intro_keyvisual.png`를 Style Reference 이미지로 고정하여 전반적인 톤과 색감을 단일 규격으로 표준화함.
2. **네이팅 키워드 표준화**: 모든 프롬프트에 `cyberpunk technical streetwear`, `neon illumination in cyan and magenta`, `cinematic lighting`을 고정값으로 삽입하여 동일한 화풍을 강제함.

### 에셋 정리 및 네이밍 규칙 (Naming Convention)
모든 생성형 AI 산출물은 다음 규칙에 따라 폴더를 구성하고 체계적으로 관리하여 통합 편집 시 재사용성과 협업성을 극대화합니다.
* **디렉토리 구조**:
  ```text
  B1-2/
  ├── assets/
  │   ├── images/  (정지 이미지 원천 에셋)
  │   ├── videos/  (AI 변환 모션 에셋)
  │   └── audios/  (생성형 사운드 및 효과음 에셋)
  └── exports/     (최종 편집 출력 영상)
  ```
* **파일명 규칙**: `scene[번호]_[에셋종류]_[태그].[확장자]`
  * 예: `scene02_image_jacket.png` (씬 2 자켓 이미지)
  * 예: `scene02_video_jacket.mp4` (씬 2 자켓 비디오 변환물)
  * 예: `scene02_audio_synth.wav` (씬 2 사운드)
