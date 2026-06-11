# 브랜드 광고 기획 및 스토리보드

## 1. 브랜드 아이덴티티

- **브랜드명**: NeoSeoul (네오서울)
- **타겟**: 10~20대 (스트릿웨어 매니아, 테크웨어 선호자, 트렌드 세터)
- **톤앤매너**: 사이버펑크, 네온사인, 우천의 서울 밤거리, 시네마틱 디스토피아와 테크웨어의 조화
- **USP (차별점)**: "서울 전통/도시 감성 + 미래적 실루엣(테크웨어)"을 결합한 한정판 스트릿 드롭
- **캠페인 목표**: 브랜드 인지도 제고 및 신규 테크웨어 라인업 런칭 홍보
- **핵심 메시지 (한 문장)**: “오늘 밤, 너의 서울을 입어라.”

---

## 2. 씬 구성 (스토리보드)

총 예상 길이: **45초**

### 씬 1: Intro (인트로)
- **씬 번호 / 씬 길이**: #1 / 6초
- **목표 메시지**: 브랜드의 세계관(서울-네온-비)을 한 컷에 각인
- **화면 구성**: 네온사인이 반사되는 젖은 도로, 그 위로 흐릿하게 걸어가는 인물의 실루엣. 전면에 브랜드 로고는 나타나지 않음.
- **내레이션 (화면 카피)**: (내레이션) "서울의 밤은, 다시 태어난다."
- **사용 도구 및 목적**: 
  - 이미지 생성: Midjourney (배경 및 비주얼 키 레퍼런스 확보)
  - 비디오 변환: Runway Gen-3 (정지 이미지에 비와 반사광의 역동적인 모션 추가)
  - 오디오 생성: Suno (빗소리 효과음이 결합된 로파이(Lo-Fi) 신스웨이브 비트 빌드)
- **입력 프롬프트**:
  - *Midjourney*: `cyberpunk neon Seoul night street, heavy rain, neon signs reflecting on wet asphalt road, deep shadows, cinematic lighting, photorealistic, 8k resolution, aspect ratio 16:9 --ar 16:9 --style raw`
  - *Runway*: `Heavy rain pouring down, realistic water droplets falling, neon reflections shimmering on the wet road, slow pan up`
  - *Suno*: `A dark cyberpunk synthwave beat with sound effects of heavy rain and distant thunder, ambient and atmospheric, lo-fi grit`
- **출력 결과 요약**: 우천 상황의 네온 감성과 도시의 차가우면서도 화려한 톤 확보.
- **결과 파일명**: `scene01_keyvisual.png`, `scene01_motion.mp4`, `scene01_bgm.mp3`

---

### 씬 2: Product Showcase - Shadow (제품 소개 - 실루엣)
- **씬 번호 / 씬 길이**: #2 / 8초
- **목표 메시지**: 독창적인 테크웨어 제품의 실루엣과 소재 질감 강조
- **화면 구성**: 골목길 네온 불빛 아래 서 있는 모델. 후드를 깊게 눌러써 얼굴은 어둡게 가려져 있으며, 방수 재킷의 매끄러운 텍스처와 네온 빛이 맺히는 디테일이 보임.
- **내레이션 (화면 카피)**: (내레이션) "빛과 어둠의 경계에서, 가장 완벽한 실루엣."
- **사용 도구 및 목적**:
  - 이미지 생성: Midjourney (일관된 디자인의 테크웨어 착장 이미지 생성)
  - 비디오 변환: Runway Gen-3 (모델의 미세한 움직임 및 의상 주름에 바인딩되는 빛 효과 구현)
  - 오디오 생성: ElevenLabs (중저음의 낮고 매력적인 남성 목소리 나레이션 합성)
- **입력 프롬프트**:
  - *Midjourney*: `A close-up shot of a model wearing a futuristic black cyberpunk techwear jacket, deep hood shadowing the face, glossy waterproof fabric texture, pink and cyan neon light highlights on the jacket creases, dark alley background, cinematic, photorealistic --ar 16:9`
  - *Runway*: `Subtle slow-motion breathing movement, neon light flickering slightly, reflecting on the jacket fabric texture`
  - *ElevenLabs (TTS)*: `In the boundary between light and shadow, the most perfect silhouette.`
- **출력 결과 요약**: 후드 재킷의 방수 재질감과 세련된 사이버펑크 룩의 시각화.
- **결과 파일명**: `scene02_model_jacket.png`, `scene02_motion.mp4`, `scene02_narration.mp3`

---

### 씬 3: Techwear Detail (테크웨어 디테일 클로즈업)
- **씬 번호 / 씬 길이**: #3 / 7초
- **목표 메시지**: 유틸리티 디테일(버클, 스트랩)을 통해 테크웨어 고유의 기능성과 스트릿 감성 표출
- **화면 구성**: 재킷에 부착된 카본 버클과 시그니처 스트랩의 접사 씬. 미세하게 흐르는 LED 발광 라인이 스며 나옴.
- **내레이션 (화면 카피)**: (화면 카피) "FUNCTION x STYLE" (자막으로만 표시)
- **사용 도구 및 목적**:
  - 이미지 생성: Midjourney (스트랩과 금속 버클의 극사실적 매크로 샷 생성)
  - 비디오 변환: Luma Dream Machine (버클 체결부 주변으로 테크니컬한 줌인 효과 적용)
  - 오디오 생성: Suno (클로즈업 타이밍에 어울리는 기계적 금속 효과음 및 비트 드롭 전환)
- **입력 프롬프트**:
  - *Midjourney*: `Macro extreme close-up of a futuristic techwear jacket buckle, tactical carbon fiber material, nylon straps, tiny glowing cyan LED line, high-tech hardware, dark moody lighting, industrial aesthetic --ar 16:9`
  - *Luma*: `Smooth macro zoom into the carbon fiber buckle, camera panning slowly to follow the strap`
- **출력 결과 요약**: 하이테크 소재감과 기능적 요소를 부각시키는 고화질 디테일 확보.
- **결과 파일명**: `scene03_detail.png`, `scene03_motion.mp4`

---

### 씬 4: Urban Movement (도시의 질주)
- **씬 번호 / 씬 길이**: #4 / 9초
- **목표 메시지**: 착용 시의 활동성과 도시 라이프스타일과의 융합 전달
- **화면 구성**: 네온 불빛 가득한 빌딩 숲 사이를 빠르게 질주하는 모델의 전신 샷. 역동적인 카메라 워킹.
- **내레이션 (화면 카피)**: (내레이션) "도시가 멈추어도, 너의 걸음은 멈추지 않는다."
- **사용 도구 및 목적**:
  - 이미지 생성: Midjourney (달리는 자세의 전신 테크웨어 모델 렌더링)
  - 비디오 변환: Runway Gen-3 (달려나가는 액션 및 역동적인 카메라 카메라 패닝 트랙킹 연출)
  - 오디오 생성: ElevenLabs (나레이션) 및 Suno (더 빨라지고 묵직해지는 테크노 신스웨이브 비트 연출)
- **입력 프롬프트**:
  - *Midjourney*: `Full-body dynamic shot of a street fashion model running through a neon cyberpunk city street at night, wearing black techwear pants and jacket, motion blur background, vibrant cyan and magenta lights, cinematic action sequence --ar 16:9`
  - *Runway*: `Dynamic camera tracking shot, the model running forward, wet asphalt reflecting light rapidly, dramatic speed`
  - *ElevenLabs (TTS)*: `Even if the city stops, your steps never do.`
- **출력 결과 요약**: 역동적인 무브먼트와 스타일리시한 전신 핏을 담은 질주 씬 생성.
- **결과 파일명**: `scene04_run.png`, `scene04_motion.mp4`, `scene04_narration.mp3`

---

### 씬 5: Transition to Climax (클라이막스 전환)
- **씬 번호 / 씬 길이**: #5 / 8초
- **목표 메시지**: 핵심 슬로건 공개 직전의 긴장감 고조 및 타겟과의 정서적 공감대 형성
- **화면 구성**: 광활하게 펼쳐진 남산타워와 네온빛 서울 전경을 빌딩 옥상에서 내려다보는 모델의 뒷모습. 바람에 자켓 자락이 흩날림.
- **내레이션 (화면 카피)**: (내레이션) "오늘 밤, 너의 서울을 입어라."
- **사용 도구 및 목적**:
  - 이미지 생성: Midjourney (서울 야경 배경과 모델의 조화)
  - 비디오 변환: Runway Gen-3 (자켓의 흩날림, 저 멀리 반짝이는 남산타워와 도시 불빛 모션 제어)
  - 오디오 생성: ElevenLabs (핵심 슬로건 보이스 오버)
- **입력 프롬프트**:
  - *Midjourney*: `A cyberpunk model standing on a skyscraper rooftop in Seoul, looking at the glowing cityscape with Namsan Tower in the far distance, windy night, techwear jacket blowing in the wind, cinematic composition, breathtaking scale --ar 16:9`
  - *Runway*: `Wind blowing through the clothes and hair, city lights in the background flickering softly, slow camera rotation`
  - *ElevenLabs (TTS)*: `Tonight, wear your Seoul.`
- **출력 결과 요약**: 압도적인 스케일의 서울 야경과 슬로건이 매칭되는 정점 씬 완성.
- **결과 파일명**: `scene05_roof.png`, `scene05_motion.mp4`, `scene05_narration.mp3`

---

### 씬 6: Outro (아웃트로 - 브랜드 로고)
- **씬 번호 / 씬 길이**: #6 / 7초 (총 45초 마무리)
- **목표 메시지**: 명확한 브랜드 인지(로고 및 CTA)와 런칭 정보 제공
- **화면 구성**: 글리치 효과가 들어간 타이포그래피로 'NeoSeoul' 브랜드 로고 등장. 하단에 'LIMITED DROP / AVAILABLE NOW' 문구와 웹사이트 URL 노출.
- **내레이션 (화면 카피)**: (내레이션) "네오서울."
- **사용 도구 및 목적**:
  - 이미지/그래픽 생성: Midjourney (글리치 효과가 가미된 브랜드 엠블럼 및 로고 레이아웃 생성)
  - 비디오 변환: Runway Gen-3 (글리치 노이즈 모션 및 빛바램 효과)
  - 오디오 생성: Suno (잔향이 강하게 남는 미래지향적 시스템 알림음 형태의 아웃트로 시그널 사운드)
- **입력 프롬프트**:
  - *Midjourney*: `Cyberpunk minimalist logo design featuring typography 'NeoSeoul', glitch effect, cyan and magenta glow, dark black background, clean vector style --ar 16:9`
  - *Runway*: `Cyberpunk glitch distortion effect on the logo, glowing neon flicker`
  - *Suno*: `A metallic glitch sound effect with a deep bass drop, ending with a lingering synthesizer chord`
  - *ElevenLabs (TTS)*: `Neo Seoul.`
- **출력 결과 요약**: 미래지향적인 글리치 로고 시퀀스로 마무리.
- **결과 파일명**: `scene06_logo.png`, `scene06_motion.mp4`, `scene06_narration.mp3`

---

## 3. 프롬프트 수정 전/후 기록 (씬 2 개선 로그)

- **수정 전 의도**: 씬 2에서 "네온 불빛 아래 서 있는 테크웨어 모델의 클로즈업 샷"을 뽑고자 함.
- **수정 전 프롬프트**:
  > `futuristic techwear model close up face in cyberpunk neon city street`
- **문제점**:
  - 인물의 이목구비 디테일이 너무 인위적으로 과장되고 미형화되어, 테크웨어가 주는 러프하고 세련된 브랜드 톤앤매너와 어긋남.
  - 옷의 테크니컬한 소재 질감(질긴 나일론, 방수 재질 등)보다 인물의 얼굴에 시선이 뺏김.
- **수정 후 프롬프트**:
  > `A close-up shot of a model wearing a futuristic black cyberpunk techwear jacket, deep hood shadowing the face, glossy waterproof fabric texture, pink and cyan neon light highlights on the jacket creases, dark alley background, cinematic, photorealistic --ar 16:9`
- **개선 사유 및 결과 변화**:
  - `deep hood shadowing the face`를 추가하여 인물의 얼굴 디테일을 의도적으로 그늘 속에 가림(실루엣화).
  - `glossy waterproof fabric texture`와 `jacket creases`를 명시하여 시선이 인물보다 브랜드 아이템(자켓)의 소재와 디테일에 머물도록 유도함.
  - 결과적으로 브랜드가 지향하는 신비롭고 시크한 다크 사이버펑크 톤앤매너 일관성을 확보함.
