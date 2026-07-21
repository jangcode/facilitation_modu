# 아이디어에서 제품까지: AI 기반 개발자를 위한 플레이북

---

> 이 가이드는 실시간 협업 시스템 설계 도구로, 전적으로 AI 기반 개발을 사용해 구축되었습니다. 이 플레이북의 모든 내용은 이론이 아니라 실제로 사용된 것입니다. 읽기를 마치면, AI를 사용해 어떤 아이디어든 빈 페이지에서 작동하는 제품으로 만드는 방법을 알게 됩니다. 더 나은 프롬프트를 쓰는 방법이 아니라, 프롬프트를 보내기 전에 더 나은 사고를 하는 방법입니다.

### 이 문서의 주요 내용

- AI 기반 개발을 위해 어떤 프로젝트든 준비하는 완전한 시스템
- 프로젝트에 맞춘 여섯 개의 컨텍스트 파일을 생성하는 AI 프롬프트
- 각 컨텍스트 파일에 채워 넣을 수 있는 빈 템플릿
- 어떤 기능이든 깨끗하게 나눠 빌드 가능한 단위로 분해하는 스펙 파일 패턴
- AI와 함께 일할 때 표류 없이 일관되게 사용하는 3-프롬프트 워크플로우
- AI가 막히거나 잘못될 때 취할 명확한 전략

### 이 폴더에 포함된 것들

```
in Omen laptop (바탕화면 Six files 있던거 기억해내라.)
📁 ai-builders-playbook/
├── README.md                    ← 이 가이드
└── templates/
    ├── CLAUDE.md                ← 진입점 템플릿
    ├── project-overview.md      ← 빈 템플릿
    ├── architecture.md          ← 빈 템플릿
    ├── code-standards.md        ← 빈 템플릿
    ├── ai-workflow-rules.md     ← 빈 템플릿
    ├── ui-context.md            ← 빈 템플릿
    └── progress-tracker.md      ← 빈 템플릿
```

각 템플릿에는 전체 구조와 각 섹션에 무엇을 넣어야 하는지에 대한 지침이 포함되어 있습니다. Part 2에 있는 AI 프롬프트를 사용해 내용을 채우세요.

### 핵심 워크플로우
- 아래는 실제 스킬이 아닙니다. 플로우의 예시입니다.
`/specify` : 과제 정의, 설명, 기능
`/plan` : 분석, 구조(아키텍처), 스택, API 설계, 실행 배포 전략
`/tasks` : 작업 분할, 진행 계획
`/implement` : 구현(반복) task by task

### 가이드 사용 방법

처음 읽을 때는 차례대로 읽으세요. 각 파트는 이전 파트 위에 쌓입니다. 그 다음에는 레퍼런스처럼 필요할 때 해당 섹션으로 점프해 사용하세요.

- **시작은 작게:** 처음에는 복잡한 툴을 쓰기보다, 현재 프로젝트 폴더에 `docs/spec.md` 같은 파일을 만들고, 기능을 구현하기 전 이 파일에 **'무엇을, 왜, 어떻게 만들 것인지'** 요약하는 것부터 시작하세요.

- **상호작용:** 사양서를 혼자 쓰는 것보다, AI와 채팅하면서 '이 사양서에 부족한 예외 케이스가 무엇인지 찾아줘'라고 질문하며 사양을 보완하는 것이 효율적입니다.
---

## Part 1: 뭘 만들기 전에

대부분의 개발자는 AI 코딩 도구를 열고 바로 타이핑을 시작합니다. 그게 실수입니다.

AI가 만들어내는 결과의 품질은 당신이 AI에 주는 ‘사고’의 품질로 결정됩니다. 명확한 시스템은 깔끔하고 유지보수 가능한 코드를 만들어내고, 모호한 아이디어는 한 시간 동안은 멋져 보여도 결국 무너집니다.
**사양(Specification) 작성 방법**은 단순히 AI에게 '이거 만들어줘'라고 모호하게 던지는 것이 아니라, **누구나(사람과 AI 모두) 이해할 수 있는 명확한 구조적 문서**를 만드는 과정입니다. 하지만 사람에게 지식과 경험이 있을 때 "명확한 구조적 문서"를 만들 수 있습니다.

### 작성 단계별 가이드

1. **초안 작성 (Specify):**
   - 처음부터 완벽한 문서를 쓰려 하지 말고, 구현하고자 하는 기능의 의도를 먼저 기술하세요. 
   - '이 기능을 만들 것'이라는 단순한 요구사항을, **입력값, 기대 결과, 제약 사항(보안, 기술 스택 등)**이 포함된 형태로 구체화합니다.

2. **공식적인 구조화:**
   - 단순히 줄글로 쓰지 말고 **마크다운(Markdown)** 형식을 사용하여 구조를 잡으세요. (예: `## 목적`, `## 요구사항`, `## 기술적 제약`, `## API 명세`)
   - 이렇게 작성된 사양은 프로젝트의 **'메모리 뱅크(Memory Bank)'** 역할을 하여, 나중에 AI가 동일한 맥락 내에서 일관되게 코드를 생성하도록 돕습니다.

3. **사람 중심의 리뷰 및 검토 (가장 중요):**
   - AI가 작성한 사양 초안을 그대로 믿지 마세요. 사양 파일이 생성되면 **사람이 직접 읽고 모호한 부분(Ambiguity)을 찾아내어 수정**해야 합니다.
   - 사양서의 목적은 '비즈니스 언어'를 '엔지니어링 결과물'로 변환하는 것이므로, 비즈니스 기획자가 봐도 이해할 수 있는지 체크하는 것이 좋습니다.

4. **저장소 커밋 (Context Preservation):**
   - 작성된 사양서는 일회용으로 쓰고 버리지 말고, **코드 저장소(Repository)에 함께 커밋**하세요. 그래야 향후 기능 수정 시 기존 사양을 참조하여 '스펙 드리프트(Spec Drift, 사양과 코드의 불일치)'를 방지할 수 있습니다.

사양 작성이 완료되면 다음 단계인 **계획(Plan) 수립**과 **작업 세분화(Tasks)**로 넘어가서 구현에 착수하게 됩니다.

프롬프트를 한 줄이라도 쓰기 전에 세 가지를 해야 합니다. 
- 모르는 것을 지나치지 마세요, 
- AI 프로젝트가 실패하는 이유를 이해하며, 
- 올바른 대화를 준비하세요.

---

### 모르는 것은 확인하세요

AI로 빌드할 때 가장 중요한 것은 당신은 설계자(아키텍트)가 되어야 한다는 것입니다. 
무엇을 만들지, 어떻게 맞물리는지, 규칙은 무엇인지, 경계는 어디에 있는지는 항상 당신은 알고 있어야 합니다. AI는 그 사고를 빠른 속도로 실행할 뿐, 그 사고를 대체하지는 않습니다.

실패하는 대부분의 프로젝트는 사고를 외주화하려 합니다. 목표를 넓게 주고 시스템 설계, 아키텍처, 컴포넌트 경계, 네이밍 규칙, 데이터 흐름을 알아서 해결하길 기대합니다. 운 좋으면 잘 되기도 하지만, 보통은 그렇지 않습니다. 잘못되면 AI 탓을 하게 됩니다.

AI로 진지한 것을 만드는 개발자는 먼저 사고를 합니다. 에이전트가 코드에 손대기 전에 시스템을 설계하고, 첫 프롬프트를 보내기 전에 규칙을 정의합니다. 그런 다음 AI를 사용해 인간보다 훨씬 빠르게 실행합니다.

"AI가 알아서 해"에서 "내가 이미 설계한 것을 AI 가 작업, 실행해"로 전환이 핵심입니다.

---

### 대부분의 AI 보조 프로젝트가 실패하는 이유

실패 모드는 두 가지입니다. 이를 이해하면 수주 간의 좌절을 피할 수 있습니다.

**실패 모드 1: 분위기 코딩 붕괴**

에이전트를 열고 넓게 원하는 것을 설명한 뒤 그냥 두면 처음 한 시간은 놀랍습니다. 코드가 빠르게 조립되고 기능이 나옵니다.

그런데 새 기능을 추가하려 하면 무언가 깨집니다. 고치면 또 다른 것이 깨집니다. 에이전트가 이전에 내린 결정들을 스스로 모순되게 바꾸기 시작합니다. 코드베이스가 싸우기 시작합니다. AI가 만든 출력을 풀어내느라 더 많은 시간을 쓰게 됩니다.

이는 에이전트가 기반으로 삼을 토대가 없기 때문입니다. 모든 결정이 추측이었고, 추측은 쌓여서 문제를 일으킵니다.

**실패 모드 2: 기능 표류(Feature Drift)**

초기 빌드는 잘됩니다. 모든 것이 작동합니다. 그런데 몇 주 후에 새 기능을 추가하려 돌아오면 에이전트가 모든 것을 잊어버립니다. 아키텍처 결정, 네이밍 규칙, 특정 로직이 작성된 이유 등을 잊고 잘못된 변경을 합니다. 의도한 패턴을 덮어씁니다.

이는 AI 에이전트가 세션 간에 메모리가 없기 때문입니다. 매 세션마다 읽어볼 문서가 없으면 에이전트는 매번 처음부터 시작합니다.

두 실패 모드는 동일한 근본 원인을 가집니다. 개발자가 에이전트가 작업할 수 있는 시스템을 제공하지 않았습니다. 해결책은 코드 작성 전에 그 시스템을 구축하는 것입니다.

---

### 코드 이전의 대화

AI 코딩 도구를 열기 전에 대화를 하세요.

에이전트와가 아니라 계획을 도와주는 AI와 대화하세요. Claude, ChatGPT, Gemini 등 어떤 것을 선호하든 됩니다. 목표는 생각을 소리 내어 말하고 AI의 질문을 통해 사고를 압박하여 시스템이 명확해질 때까지 다듬는 것입니다.

이 대화가 작업입니다. 시니어 엔지니어들이 빌드 전에 머릿속이나 화이트보드에서 하던 일을 AI와 함께 외부화하는 것입니다. 가정들을 도전 받고, 결정을 빠르게 검증할 수 있습니다.

그 대화에서 다룰 내용 예시:

- 이 시스템은 실제로 무엇을 하는가?
- 누가 사용하며 그들의 핵심 요구는 무엇인가?
- 처음부터 끝까지의 핵심 사용자 흐름은 무엇인가?
- 기술적으로 가장 복잡한 부분은 무엇인가?
- 무엇이 잘못될 수 있는가?
- 기술 선택은 무엇이며 이유는 무엇인가?
- 명확하게 범위에서 제외할 것은 무엇인가?

서둘지 마세요. 대화 중에 시스템이 머릿속에서 명확해질수록 이후의 모든 것이 더 좋아집니다.

---

### AI와 아이디어를 논의하는 방법

아래 프롬프트는 어떤 프로젝트에 대해서도 대화를 시작할 때 사용할 수 있습니다:

```
애플리케이션에 대한 아이디어가 있습니다.
제가 개발을 시작하기 전에 이 아이디어를 함께 정리하도록 도와주세요.
아이디어는 다음과 같이 작성하세요: [2-3문장으로 아이디어를 설명하세요]

저에게 한 번에 하나씩 질문하여 다음 내용을 명확히 하는 데 도와주세요:

- 핵심 사용자 흐름
- 기술적으로 가장 복잡한 부분
- 데이터 및 저장 요구 사항
- 인증 및 접근 모델
- 범위 안에 있는 것과 일부러 제외된 것
- 기술 선택과 그 이유

제가 모호하게 답할 때나 잠재적 문제가 보일 때는 반박해 주세요.
코드를 작성하기 전에 시스템에 대해 명확하게 생각할 수 있도록 도와주세요.
```

대화가 끝날 때까지 질문을 이어가세요. 모든 질문에 망설임 없이 답할 수 있을 때 문서로 옮길 준비가 된 것입니다.

---

### 코딩 도구를 열기 전에 답해야 할 질문들

열기 전에 다음 질문들에 답할 수 있어야 합니다:

**제품 측면**

- 이 애플리케이션은 한 문장으로 무엇을 하는가?
- 주요 사용자는 누구이며 핵심 가치는 무엇인가?
- 회원가입부터 핵심 가치 도달까지의 단계별 흐름은?
- 첫 버전의 가장 중요한 세 가지 기능은 무엇인가?
- 명확하게 범위에서 제외된 항목은 무엇인가?

**기술 측면**

- 전체 기술 스택과 각 선택의 이유는?
- 데이터는 어디에 저장되는가(데이터베이스, 파일 스토리지, 캐시)?
- 인증은 어떻게 작동하는가?
- 시스템 경계는 무엇이며 각 폴더는 어떤 책임을 지는가?
- 코드베이스가 절대 위반하면 안 되는 규칙은 무엇인가?

**디자인 측면**

- 시각적 언어(색상, 타이포그래피, 간격)는 무엇인가?
- 어떤 UI 컴포넌트 라이브러리를 사용하는가?
- 전체적인 레이아웃은 어떻게 생겼는가?

**프로세스 측면**

- 주요 기능들은 어떻게 빌드 가능 단위로 나뉘는가?
- 어떤 순서로 단위들을 빌드해야 하는가?
- 각 단위의 ‘완료’ 기준은 무엇인가?

이 질문들에 답할 수 있다면 빌드할 준비가 된 것입니다. 답할 수 없다면 계획 AI와 더 대화하세요.

---

## Part 2: 기초를 세우기

시스템이 머릿속에서 명확해지면, 그것을 문서로 옮깁니다.

여기서 6개의 Context pattern이 나옵니다. 빈 페이지 앞에서 문서를 쓰려고 애쓰는 대신, 계획 대화의 출력을 프로젝트 전체 수명 동안 함께할 문서 집합으로 정리합니다.

이 여섯 파일은 에이전트가 작업을 시작하기 전에 읽는 파일들입니다. 에이전트가 프로젝트를 이해하고 일관되게 동작하도록 충분한 정보를 제공합니다.

작은 주말 프로젝트는 네 파일이면 충분할 수 있고, 복잡한 다중 팀 SaaS는 여덟 파일이 필요할 수 있습니다. 변하지 않는 원칙은 같으며: 에이전트가 작업하기 전에 프로젝트가 무엇인지, 어떻게 맞물리는지, 규칙은 무엇인지, 현재 상태는 무엇인지 알려줘야 합니다.

templates 폴더의 파일들은 실제적인 예시입니다. 이 섹션과 함께 읽어 각 파일이 실제로 어떻게 구성되는지 확인하세요.

### AI로 각 파일 생성하는 방법

이 파일들을 처음부터 손으로 쓰지 마세요. 생성합니다.

Part 1의 대화 출력을 각 파일의 입력으로 사용하세요. 각 파일을 만들 때 계획 AI를 열고 아래의 프롬프트를 사용해 초안을 만들게 하세요. 검토하고 수정해 프로젝트를 정확히 반영하도록 만드세요.

목표는 정확성입니다. 이 파일들은 프로젝트가 진화하면서 계속 바뀝니다. 알고 있는 만큼 시작하고, 결정이 내려질 때마다 업데이트하세요.

---

#### project-overview.md

**무엇을 하는가**

무엇을 만드는지와 그 이유를 정의합니다. 목표, 핵심 사용자 흐름, 기능, 범위 경계, 성공 기준을 포함합니다.

**왜 중요한가**

이 파일은 스펙이 모호할 때 에이전트가 의도를 이해하는 데 사용하는 파일입니다. 없으면 에이전트는 모호한 부분을 추측으로 채웁니다. 있으면 모호한 요구사항이 제품 비전에 따라 해석됩니다.

범위에서 제외된 항목 섹션은 특히 중요합니다. 당신이 만들지 않을 것을 명시적으로 적어 두면, 에이전트가 필요 없는 종속성을 제안하거나 기능 코드를 작성하지 않습니다. 범위 확장은 프로젝트를 망칩니다. 이 파일은 에이전트가 그 확장을 도와주지 못하게 막습니다.

**🤖 AI 프롬프트**

```
Based on our conversation about my project, help me write
a ./context/project-overview.md file.
It should include:

- A one paragraph overview of what the application does
- A numbered list of goals
- A step-by-step core user flow from start to finish
- A features section broken down by category
- An in-scope section listing what we are building
- An out-of-scope section listing what we are not building
- A success criteria section defining what done looks like

My project: [paste your idea and key decisions from your
planning conversation]
Write it in plain Markdown. Be specific and concrete.
Avoid vague language.
```
```
제 프로젝트에 대한 대화를 바탕으로, 다음 내용을 포함하여 ./context/project-overview.md 파일을 작성해 주세요.

- 애플리케이션의 기능에 대한 한 단락 분량의 개요
- 목표 목록(번호 매기기)
- 시작부터 완료까지의 핵심 사용자 흐름(단계별)
- 카테고리별로 분류된 기능 섹션
- 개발 범위 내 항목 목록
- 개발 범위 외 항목 목록
- 완료 기준을 정의하는 성공 기준 섹션

제 프로젝트: [계획 회의에서 논의된 아이디어 및 주요 결정 사항을 붙여넣으세요]
Markdown 형식으로 작성해 주세요. 구체적이고 명확하게 작성해 주세요.
모호한 표현은 피해주세요.
```

**좋은 출력 예**

목표는 감성적이지 않고 측정 가능해야 합니다. 사용자 흐름은 단계별로 빈틈 없이 작성되어야 합니다. 범위에서 제외된 항목 목록은 명시적이고 상세해야 합니다. 성공 기준은 "보기 좋다"가 아니라 "로그인한 사용자가 프로젝트를 생성하고 열 수 있다"처럼 검증 가능한 것이어야 합니다.

---

#### architecture.md

**무엇을 하는가**

전체 기술 스택, 시스템 경계, 저장 모델, 인증 모델, 그리고 코드베이스가 절대 위반해서는 안 되는 불변 조건을 정의합니다.

**왜 중요한가**

이 파일은 시스템에서 가장 중요한 파일입니다. 이 파일이 없으면 에이전트는 합리적으로 보이는 아키텍처 결정을 내리지만, 그것은 점차 코드베이스를 오염시킵니다. 올바른 레이어에 두지 않고, 소유권 검사를 건너뛰고, 잘못된 도구를 선택합니다.

불변 조건 섹션이 좋은 아키텍처 파일과 훌륭한 아키텍처 파일을 구분합니다. 불변 조건은 시스템이 절대 위반해서는 안 되는 규칙입니다. 예: "요청 핸들러는 장기 실행 AI 작업을 수행하지 않는다." 또는 "모든 변이 경계에서 인증이 적용된다." 불변 조건이 없으면 위반이 조용히 발생합니다. 불변 조건이 있으면 위반이 즉시 드러납니다.

**🤖 AI 프롬프트**

```
Help me write an architecture.md file for my project.
It should include:

- A stack table with each layer, technology, and its role
- System boundaries which folder owns which responsibility
- Storage model what goes in the database vs file storage vs cache
- Auth and access model how authentication and ownership work
- Any AI or background task models if relevant
- Invariants — rules the codebase must never violate

My stack and key decisions: [paste your technology choices
and architectural decisions from your planning conversation]
Write it in plain Markdown with tables where appropriate.
Be specific. The invariants section should have at least
four rules.
```
```
제 프로젝트의 architecture.md 파일을 작성하는 데 도움을 주세요.
다음 내용이 포함되어야 합니다.

- 각 계층, 기술 및 역할에 대한 스택 테이블
- 시스템 경계: 각 폴더가 어떤 책임을 갖는지
- 스토리지 모델: 데이터베이스, 파일 스토리지, 캐시 중 어디에 저장할지
- 인증 및 접근 모델: 인증 및 소유권 작동 방식
- 관련이 있다면 AI 또는 백그라운드 작업 모델
- 불변 조건: 코드베이스가 절대 위반해서는 안 되는 규칙

제 스택 및 주요 결정 사항: [기술 선택 사항 및 계획 회의에서 논의된 아키텍처 결정 사항]
필요에 따라 표를 사용하여 일반 마크다운 형식으로 작성해 주세요.

구체적으로 작성해 주세요. 불변 조건 섹션에는 최소
4개 이상의 규칙이 포함되어야 합니다.
```

**좋은 출력 예**

스택 표는 각 기술의 역할을 명확하게 포함합니다. 시스템 경계는 정확한 폴더 이름과 책임을 명시합니다. 저장 모델은 어떤 것이 어디에 저장되는지 명확하게 설명합니다. 불변 조건은 지침이 아니라 규칙으로 작성됩니다.

---

#### code-standards.md

**무엇을 하는가**

TypeScript 관례, 프레임워크 패턴, API 라우트 구조, 파일 구성, 스타일 규칙을 정의합니다.

**왜 중요한가**

코드 표준이 없으면 에이전트가 점차 다른 방향으로 흘러갑니다. 다섯 번째 단위의 패턴은 스무 번째 단위의 패턴과 다르게 보입니다. 타입 처리 방식이 일관되지 않습니다. 컴포넌트 구조가 기능마다 다르게 작성됩니다. 개별적으로는 괜찮아 보이지만, 함께 모이면 읽기 어렵고 확장하기 어렵고 인계하기 어려운 코드베이스가 됩니다.

**🤖 AI 프롬프트**

```
Help me write a code-standards.md file for my project.
It should include:

- Coding conventions for TypeScript and the framework you are using
- Folder and file organization rules
- API route and endpoint naming conventions
- Component structure and UI component rules
- Testing conventions and when to add tests
- Refactoring and cleanup expectations
- Any specific linting or formatting rules

My project: [paste your idea and key decisions from your
planning conversation]
Write it in plain Markdown. Be specific and concrete.
Avoid vague language.
```
```
제 프로젝트의 code-standards.md 파일을 작성하는 데 도움을 주세요.
다음 내용이 포함되어야 합니다.

- TypeScript 및 사용 중인 프레임워크의 코딩 규칙
- 폴더 및 파일 구성 규칙
- API 라우트 및 엔드포인트 명명 규칙
- 컴포넌트 구조 및 UI 컴포넌트 규칙
- 테스트 규칙 및 테스트 추가 시점
- 리팩토링 및 코드 정리 계획
- 특정 린팅 또는 포맷팅 규칙

프로젝트 정보: [프로젝트 아이디어 및 기획 회의에서 결정된 주요 사항]
Markdown 형식으로 작성해 주세요. 구체적이고 명확하게 작성해 주시고, 모호한 표현은 피해주세요.
```


**좋은 출력 예**

코드 표준은 형식적이지 않습니다. 서로 다른 기능에서 동일한 패턴을 유지해야 합니다. 네이밍 규칙은 일관되어야 합니다. 테스트 규칙은 무엇을 어디에 작성해야 하는지 알려야 합니다. 스타일 규칙은 과도한 자유를 주지 않고, 에이전트가 단일 방식으로 코드를 생성할 수 있도록 해야 합니다.

---

#### ui-context.md

**무엇을 하는가**

시각적 언어를 정의합니다. 색상 토큰, 타이포그래피, 테두리 반경 스케일, 컴포넌트 라이브러리 관례, 레이아웃 패턴, 아이콘 사용을 포함합니다.

**왜 중요한가**

이 파일이 없으면 에이전트는 모든 시각적 결정을 추측합니다. 원시 색상 값(raw hex)을 사용하고, 일관되지 않은 테두리 반경을 적용하며, 기능마다 다른 컴포넌트 패턴을 섞어 씁니다. 결과는 마치 열 명의 다른 개발자가 만든 UI처럼 보입니다.

이 파일이 있으면 에이전트는 시각적 결정을 스스로 내리지 않습니다. 사양을 읽습니다.

**만드는 방법**

이 파일은 다른 파일과 다릅니다. 단순히 계획 대화에서 생성하는 것이 아닙니다. 먼저 디자인하고, 그다음 문서화합니다.

대화를 이렇게 시작하세요:

```
I'm building [describe your app]. Help me design a
color token system for it.
The aesthetic I want: [describe the feel — dark/light,
technical/friendly, minimal/rich, etc.]
Generate:

- A complete color palette with semantic token names
  and hex values
- Typography recommendations
- Border radius scale
- Any AI or accent color variants if relevant

Give me the output as a Markdown table I can paste
into my ui-context.md file.
```
```
[앱 설명]을 개발 중입니다. 이 앱에 어울리는 색상 토큰 시스템을 디자인하는 데 도움을 주세요.
원하는 디자인은 다음과 같습니다. [느낌 설명 - 어둡거나 밝은 느낌,
기술적이거나 친근한 느낌, 미니멀하거나 풍부한 느낌 등]
다음 항목을 생성해 주세요.

- 의미 토큰 이름과 16진수 값을 포함한 전체 색상 팔레트

- 타이포그래피 추천
- 테두리 반경 크기
- 필요한 경우 AI 또는 강조 색상 변형

결과물을 ui-context.md 파일에 붙여넣을 수 있는 Markdown 테이블 형식으로 제공해 주세요.
```

그런 다음 이 출력 위에 컴포넌트 라이브러리 관례, 레이아웃 패턴, 아이콘 라이브러리를 더하세요.

**좋은 출력 예**

모든 색상은 원시 헥스 값이 아니라 이름이 있는 토큰입니다. 에이전트는 색상을 발명할 필요가 없어야 합니다. 가능한 모든 색상 결정이 이 파일에 있어야 합니다. 레이아웃 패턴은 애플리케이션의 실제 구조를 설명해야 합니다 — 사이드바 동작, 모달 패턴, 네비게이션 바 구조.

---

#### ai-workflow-rules.md

**무엇을 하는가**

에이전트가 빌드하는 동안 어떻게 행동해야 하는지를 정의합니다. 범위 규칙, 언제 작업을 나눌지, 요구사항이 누락되었을 때 어떻게 처리할지, 다음 단계로 넘어가기 전에 어떻게 검증할지를 포함합니다.

**왜 중요한가**

이 파일은 에이전트를 규율 있게 만드는 파일입니다. 이 파일이 없으면 에이전트는 너무 넓게 작업하고, 관련 없는 부분을 하나의 프롬프트에 합치고, 누락된 요구사항을 추측하고, 검증을 건너뜁니다. 이 파일이 있으면 에이전트는 자기 영역에 머무르고, 사양에 정확히 맞게 수행합니다.

**🤖 AI 프롬프트**

```
Help me write an ai-workflow-rules.md file for my project.
It should define how an AI coding agent should behave
while building this project. Include:

The overall approach (spec-driven, incremental)
Scoping rules (one unit at a time, no speculative changes)
When to split work into smaller steps
How to handle missing or ambiguous requirements
Which files should not be modified without explicit
instruction (e.g. generated UI library components)
How to keep documentation in sync with implementation
Verification checklist before moving to the next unit

Write it as direct instructions to the agent. Not guidelines
— rules. Use imperative language.
```
```
제 프로젝트에 사용할 ai-workflow-rules.md 파일을 작성하는 데 도움을 주세요.
이 파일은 AI 코딩 에이전트가 프로젝트를 빌드하는 동안 어떻게 동작해야 하는지를 정의해야 합니다. 다음 내용을 포함하세요.

전반적인 접근 방식 (사양 기반, 점진적)
범위 설정 규칙 (한 번에 하나의 단위만 작업, 추측성 변경 금지)
작업을 더 작은 단계로 분할해야 하는 시점
누락되거나 모호한 요구사항 처리 방법
명시적인 지시 없이는 수정해서는 안 되는 파일 (예: 생성된 UI 라이브러리 구성 요소)
문서와 구현을 동기화하는 방법
다음 단위로 넘어가기 전 검증 체크리스트

에이전트에 대한 직접적인 지침 형식으로 작성해 주세요. 가이드라인이 아닌 규칙이어야 합니다.
명령형 언어를 사용하세요.
```

**좋은 출력 예**

직접 명령형으로 작성되어야 합니다. "한 번에 하나의 기능 단위만 작업하라"가 아니라 "한 번에 하나의 기능 단위만 작업하라"처럼 작성합니다. 누락된 요구사항 섹션은 구체적이어야 하며, 모호한 부분을 추측하게 두지 않고 에이전트가 정확히 무엇을 해야 하는지 알려줍니다.

---

#### progress-tracker.md

**무엇을 하는가**

현재 단계, 완료된 것, 진행 중인 것, 다음에 할 것, 열린 질문, 아키텍처 결정, 세션 노트를 추적합니다.

**왜 중요한가**

이 파일은 빌드 동안 계속해서 변경되는 유일한 파일입니다. 장기 빌드에서는 가장 중요한 파일입니다.

AI 에이전트는 세션 간에 메모리가 없습니다. 새 세션을 열 때마다 에이전트는 처음부터 시작합니다. 프로그레스 트래커는 한 번의 프롬프트로 전체 컨텍스트를 복원하는 방법입니다. 진입 파일을 읽고 재개하라는 한 줄의 지시를 주면, 에이전트는 프로젝트가 어디에 있는지, 어떤 결정이 내려졌는지, 다음에 무엇을 해야 할지를 압니다.

이 파일이 없으면 에이전트에게 매번 처음부터 자신의 프로젝트를 15분 동안 다시 설명하게 됩니다. 이 파일이 있으면 몇 초 안에 다시 움직일 수 있습니다.

**설정 방법**

다른 다섯 파일과 달리 프로그레스 트래커는 빈 상태로 시작합니다. 이 템플릿을 복사하고 처음 두 섹션을 채우세요:

```markdown
# Progress Tracker

Update this file after every meaningful implementation change.

## Current Phase

- [phase name]

## Current Goal

- [what you are building right now]

## Completed

- None yet.

## In Progress

- None yet.

## Next Up

- [first unit to build]

## Open Questions

- [any unresolved decisions]

## Architecture Decisions

- [decisions made that affect the system design]

## Session Notes

- [context needed to resume in the next session]
```

에이전트는 각 단위가 끝날 때 이 파일을 업데이트합니다. 당신은 아키텍처 결정을 내리거나 열린 질문이 해결될 때 이 파일을 업데이트합니다. 프로젝트가 끝날 때쯤이면 이 파일은 내려진 모든 결정과 그 이유를 완벽하게 기록한 문서가 됩니다.

---

### AGENTS.md 진입점

여섯 개 파일이 있으면 한 파일이 더 필요합니다 — 코딩 에이전트가 무엇을 하기 전에 어디를 봐야 하는지 알려주는 진입점 파일입니다.

모든 주요 코딩 에이전트는 자체 규칙을 가지고 있습니다. Claude Code는 `CLAUDE.md`를 읽습니다. Codex와 GitHub Copilot은 `AGENTS.md`를 사용합니다 — Next.js에서 새 프로젝트를 초기화하면 자동으로 생성되기도 합니다. Cursor는 `.cursorrules`를 사용합니다. Windsurf는 자체 규칙을 사용합니다.

사용하는 코딩 에이전트에 맞는 파일 이름을 사용하세요. 내용과 목적은 동일합니다. 루트에 있는 한 파일이 매 세션마다 먼저 읽히는 것입니다.

템플릿은 다음과 같습니다:

```markdown
## Application Building Context

Read the following files in order before implementing
or making any architectural decision:

1. `context/project-overview.md` — product definition,
   goals, features, and scope
2. `context/architecture.md` — system structure,
   boundaries, storage model, and invariants
3. `context/ui-context.md` — theme, colors, typography,
   and component conventions
4. `context/code-standards.md` — implementation rules
   and conventions
5. `context/ai-workflow-rules.md` — development workflow,
   scoping rules, and delivery approach
6. `context/progress-tracker.md` — current phase,
   completed work, open questions, and next steps

Update `context/progress-tracker.md` after each
meaningful implementation change.

If implementation changes the architecture, scope, or
standards documented in the context files, update the
relevant file before continuing.
```

이 파일은 전체 시스템을 작동하게 만드는 지시입니다. 이 파일이 없으면 에이전트가 컨텍스트 파일을 건너뛰거나, 추측을 하거나, 당신이 정의한 아키텍처와 다르게 흘러갈 수 있습니다. 이 파일이 있으면 매 세션이 같은 방식으로 시작합니다. 전체 컨텍스트, 정의된 시스템, 명확한 규칙.

---

### 포함된 템플릿을 사용하는 방법

이 다운로드의 `templates/` 폴더에는 자신의 프로젝트를 위해 바로 채울 수 있는 모든 컨텍스트 파일의 빈 버전이 들어 있습니다.

사용 방법은 다음과 같습니다:

1. `templates/` 폴더 전체를 프로젝트 루트로 복사하고 `context/`로 이름을 바꿉니다.
2. 각 파일을 열고 이 가이드의 AI 프롬프트를 사용해 해당 프로젝트에 맞는 내용을 생성합니다.
3. 각 파일이 시스템을 정확하게 나타내도록 검토하고 다듬습니다.
4. 제공된 템플릿을 사용해 루트에 `CLAUDE.md`를 추가합니다.

템플릿은 구조를 제공합니다. Part 2의 AI 프롬프트는 내용을 제공합니다. 당신의 계획 대화는 AI가 올바르게 채우는 데 필요한 모든 것을 제공합니다.

실제 프로덕션 급 컨텍스트 파일이 어떻게 구성되는지 보고 싶다면, 무료 비디오 키트에 포함된 전체 Ghost AI 컨텍스트 파일을 확인하세요. 비디오 설명의 링크를 참조하세요.

---

## Part 3: 빌드를 분해하기

컨텍스트 파일은 준비되었습니다. 이제 단 하나의 질문에 답해야 합니다. 정확히 무엇을, 어떤 순서로 빌드할 것인지, 각 작업의 완료 기준은 무엇인지입니다.

이것이 스펙 기반 개발입니다.

에이전트를 열고 기능별로 아이디어를 떠올리며 프롬프트를 보내는 대신, 빌드를 시작하기 전에 전체를 계획하고 각 작업을 구체적이고 검증 가능한 단위로 나눕니다. 각 단위는 스펙을 가집니다. 각 스펙은 완료가 어떤 모습인지 정확히 정의합니다.

대부분의 개발자는 여기서 멈춥니다. 컨텍스트 파일을 완성하고 즉시 프롬프트를 보내기 시작합니다. 그 결과 시작은 빠르지만 중간부터는 혼란스러워집니다. 조각이 맞지 않기 때문입니다.

스펙 기반 개발은 이를 바로잡습니다. 모든 단위가 계획됩니다. 모든 의존성이 순서대로 배치됩니다. 모든 기능은 에이전트가 손대기 전에 명확한 종료 상태를 갖습니다.

---

### 빌드를 단위로 분해하는 방법

단위는 하나의 범위가 정해진, 검증 가능한 작업입니다. 한 번의 집중된 세션에서 빌드할 수 있을 만큼 충분히 작고, 완료 상태가 명확할 만큼 구체적이어야 합니다.

"대시보드를 빌드하라"는 단위가 아닙니다. 그것은 단계입니다.

단위는 다음과 같습니다. "프로젝트 사이드바를 My Projects와 Shared 탭으로 만들고, 빈 상태 플레이스홀더를 추가하며, 열고 닫는 동작을 구현한다. API 호출은 아직 없다."

**좋은 단위의 규칙:**

- 하나의 눈에 보이는 검증 가능한 결과를 만든다
- 하나의 시스템 경계 내에 머문다 — UI 변경, 데이터베이스 변경, 백그라운드 작업을 한 단위에 섞지 않는다
- 완료로 간주되기 전에 참이어야 하는 조건 목록이 있다
- 다른 단위에 속하는 결정을 내려야 하지 않고, 한 번의 집중된 세션에서 빌드할 수 있다

**AI를 사용해 분해하는 방법:**

```
I'm building [your application]. My context files define
the full architecture and feature set.
Help me break the entire build into units following
these rules:

- Each unit produces one visible result
- Each unit stays within one system boundary
- Dependencies are introduced just in time, don't
  install or build something before it is needed
- Units that always get done together in the same
  session should be merged into one unit
- Units with no standalone visible result should be
  merged with adjacent units

Here is my feature list: [paste your features from
project-overview.md]
Here is my stack: [paste your stack from architecture.md]
Output a numbered list of units in build order. For each
unit include: unit number, unit name, what it builds,
and any dependencies that must exist first.
```

결과를 주의 깊게 검토하세요. 순서가 맞지 않으면 재정렬하세요. 너무 작아서 독립적으로 존재할 수 없는 단위는 병합하고, 너무 많은 일을 하려는 단위는 분할하세요.

**결과는 당신의 빌드 플랜입니다.** `context/specs/00-build-plan.md`로 저장하세요. 이 파일은 첫 프롬프트를 보내기 전에 전체 시스템이 설계되었음을 증명합니다.

---

### 스펙 파일 패턴

빌드 플랜의 각 단위는 자체 스펙 파일을 가집니다. 스펙 파일은 해당 단위에 대한 완전한 지침 세트이며, 모호한 프롬프트를 대체합니다.

코딩 에이전트는 스펙 파일을 읽고 정확히 적힌 대로 구현합니다. 그 이상도 그 이하도 아닙니다.

잘 작성된 스펙 파일은 다섯 섹션을 가집니다:

**1. 목표**

한두 문장. 이 단위가 완료되었을 때 어떤 결과물을 만드는지 구체적으로 설명합니다.

_나쁜 예:_ "인증 페이지를 만든다."

_좋은 예:_ "데스크톱에서 투패널 레이아웃을 사용하고 모바일에서는 폼 전용 레이아웃을 사용하는 로그인 및 회원가입 페이지를 생성한다. 미들웨어 대신 proxy.ts를 사용해 경로 보호를 구현한다."

**2. 디자인**

이 단위에 특화된 시각적 및 구조적 결정입니다. 관련이 있다면 ui-context.md 토큰을 참조하세요. 이렇게 하면 에이전트가 시각적 추측을 하지 않습니다.

**3. 구현**

하나의 컴포넌트나 시스템 경계마다 하위 섹션으로 나눕니다. 각 섹션은 무엇을 어떻게 빌드할지 정확히 알려줍니다. 완료된 상태에 대해서 모호함이 없을 만큼 충분히 자세히 작성하세요.

**4. 의존성**

이 단위가 필요로 하는 패키지를 나열합니다. 이미 설치된 항목이 아니라 추가로 설치해야 하는 것만 적습니다. 에이전트가 알아서 추측하지 못하도록 명시적으로 작성하세요.

**5. 완료 검증 체크리스트**

이 단위가 완료되었을 때 참이어야 하는 구체적인 조건 목록입니다. 에이전트가 이를 기준으로 체크하고, 당신도 다음으로 넘어가기 전에 확인합니다.

**스펙 파일 템플릿:**

```markdown
# Unit NN: [Feature Name]

## Goal

One or two sentences describing the concrete output
of this unit.

## Design

Visual and structural decisions specific to this unit.
Reference ui-context.md tokens where relevant.

## Implementation

### [Component or Sub-section Name]

Detailed description of what to build.

### [Next sub-section]

Description.

## Dependencies

- package-name (reason)

## Verify when done

- [ ] Condition one
- [ ] Condition two
- [ ] No TypeScript errors
- [ ] No console errors
- [ ] Responsive at mobile and desktop
- [ ] npm run build passes
```

---

### AI를 사용해 기능 스펙 생성하기

스펙 파일도 처음부터 쓰지 마세요. 기능을 구현하기 직전에 생성합니다.

 준비가 되면 계획 AI와 짧게 대화하세요. 다음을 공유합니다:

- project-overview.md와 architecture.md
- 이 단위에서 무엇을 빌드할지
- 적용할 구체적인 결정이나 제약

그런 다음 스펙 파일을 작성해 달라고 요청합니다:

```
Here is my project overview: [paste project-overview.md]
Here is my architecture: [paste architecture.md]
I want to implement: [describe the feature]
Write a detailed spec file for this feature following
this structure:

- Goal (1-2 sentences, specific and concrete)
- Design (visual and structural decisions)
- Implementation (broken into sub-sections)
- Dependencies (packages to install)
- Verification checklist

Be as specific as possible. If anything is unclear,
ask me questions before writing the spec.
```

이미 무엇을 빌드할지 알고 있다면, 대략적인 설명을 직접 쓰고 AI에게 제대로 구조화된 스펙 파일로 바꿔 달라고 해도 됩니다.

어쨌든, 스펙이 구체적일수록 코딩 에이전트의 결과가 좋아집니다. 모호한 스펙은 모호한 코드를 만듭니다. 구체적인 스펙은 깔끔하고 예측 가능한 구현을 만듭니다.

하나의 기능에 스펙 파일이 하나 필요할 수도 있고, 세 개가 필요할 수도 있습니다. 복잡도가 기준이 될 뿐, 고정 규칙은 아닙니다.

---

### 빌드 플랜 — 단위의 순서 정하기

단위의 순서는 대부분의 개발자가 생각하는 것보다 중요합니다. 순서를 잘못 정하면, 아직 존재하지 않는 기반 위에 기능을 쌓거나, 사용할 준비가 되지 않은 기반을 먼저 만들게 됩니다.

**순서를 정하는 규칙:**

**의존성 먼저.** 기능 B가 기능 A 위에 지어져야 한다면 A가 먼저 옵니다. 존재하지 않는 것 위에 구축하지 마세요.

**보안이 기능보다 먼저.** 인증과 접근 제어는 이를 보호하는 기능보다 먼저 구축해야 합니다. 접근 제어 모델이 없는데 협업 캔버스를 만드는 것은 보안 없는 기반 위에 짓는 것입니다.

**백엔드가 프런트엔드 연결보다 먼저.** API 라우트를 먼저 구축하고, 그다음 UI를 연결하세요. 둘을 한 단위에 섞으면 에이전트가 서로 다른 영역에서 추측할 여지가 너무 커집니다.

**UI 뼈대는 실제 데이터 이전에.** 플레이스홀더 데이터로 컴포넌트 구조를 먼저 만들고, 그다음 실제 API 호출을 연결하세요. 이렇게 하면 데이터 계층이 없더라도 UI가 작동하는지 검증할 수 있습니다.

**의존성은 필요한 시점에 설치하세요.** 실제 동작을 처음으로 여는 단위에서만 패키지를 설치합니다. 모든 것을 한꺼번에 설치하면 컨텍스트가 복잡해지고 에이전트가 아직 사용하지 않아야 할 도구를 사용하려 들 수 있습니다.

**빌드 순서를 검증하는 방법:**

단위 목록을 검토하며, 각 단위가 이전 단위에서 필요한 모든 것을 이미 갖추고 있는지 확인하세요. 아니면 순서를 재배치하세요.

또한 두 인접 단위가 항상 같은 세션에서 완료되어야 하고 중간에 독립적인 결과가 없다면 하나로 병합하세요.

순서가 맞으면, 모든 단위가 이전 단위 위에 깔끔하게 쌓입니다. 어떤 단위도 앞으로 뛰어넘을 필요가 없고, 어떤 단위도 세 단위 뒤에야 작동하는 상태를 남기지 않습니다.

---

## 간단한 워크플로우

컨텍스트 파일이 준비되었습니다. 빌드 플랜이 정해졌습니다. 첫 스펙 파일이 작성되었습니다.

**구현을 위한 한 가지 프롬프트:**

```
Read context/specs/NN-feature-name.md.
Update context/progress-tracker.md to mark this as
in progress.
Implement it exactly as specified.
Do not go beyond the scope of this unit.
```

**무언가 잘못됐을 때 수정하는 한 가지 프롬프트:**

```
The [specific element] does not match the spec.
Expected: [what the spec says].
Current: [what was built].
Fix only this. Do not change anything else.
```

**마무리할 때 한 가지 프롬프트:**

```
Implementation is complete and verified.
Mark unit NN complete in context/progress-tracker.md.
Push branch feat/NN-feature-name to GitHub.
```

이 사이클은 빌드 플랜의 각 단위마다 반복됩니다. 컨텍스트 파일은 에이전트를 일관되게 유지합니다. 스펙 파일은 각 단위를 집중하게 합니다. 진행 추적기는 모든 세션을 실제 프로젝트 상태에 맞춥니다.


---
## templates

### CLAUDE.md

```
## 애플리케이션 구축 컨텍스트

구현하기 전에 또는 아키텍처 결정을 내리기 전에
다음 파일들을 순서대로 읽으세요:

1. `context/project-overview.md` — 제품 정의,
   목표, 기능, 범위
2. `context/architecture.md` — 시스템 구조,
   경계, 저장소 모델, 불변성
3. `context/ui-context.md` — 테마, 색상, 타이포그래피,
   컴포넌트 규칙
4. `context/code-standards.md` — 구현 규칙
   및 규칙
5. `context/ai-workflow-rules.md` — 개발 워크플로우,
   범위 규칙, 전달 접근방식
6. `context/progress-tracker.md` — 현재 단계,
   완료된 작업, 해결할 질문, 다음 단계

의미 있는 구현 변경 후마다
`context/progress-tracker.md`를 업데이트하세요.

구현이 컨텍스트 파일에 기록된 아키텍처, 범위,
또는 표준을 변경하면, 계속하기 전에 관련 파일을
업데이트하세요.
```

### context/ai-workflow-rules.md

```
# AI 워크플로우 규칙

## 접근 방식

[전체 개발 접근 방식을 설명하세요 — 예: 사양 기반 워크플로우를 사용하여 이 프로젝트를 점진적으로 빌드합니다.
컨텍스트 파일은 무엇을 빌드할지, 어떻게 빌드할지, 현재 진행 상황을 정의합니다. 항상 이러한 사양에 따라
구현하세요 — 처음부터 동작을 추론하거나 발명하지 마세요.]

## 범위 규칙

- 한 번에 하나의 기능 단위에 대해 작업
- 큰 추측성 변경보다 작고 검증 가능한 증분 선호
- 단일 구현 단계에서 관련 없는 시스템 경계를 결합하지 마세요

## 작업을 분할할 시기

다음을 결합하는 경우 구현 단계를 분할하세요:

- [관심사 1 — 예: UI 변경 및 백그라운드 작업 변경]
- [관심사 2 — 예: 여러 관련 없는 API 경로]
- [관심사 3 — 예: 컨텍스트 파일에 명확하게 정의되지 않은 동작]

변경을 빠르게 끝에서 끝까지 검증할 수 없으면,
범위가 너무 넓습니다 — 분할하세요.

## 누락된 요구사항 처리

- 컨텍스트 파일에 정의되지 않은 제품 동작을 발명하지 마세요
- 요구사항이 모호하면, 구현하기 전에 관련 컨텍스트 파일에서 해결하세요
- 요구사항이 누락되면, 계속하기 전에 `progress-tracker.md`에 미결 질문으로 추가하세요

## 보호된 파일

명시적으로 지시되지 않는 한 다음을 수정하지 마세요:

- [예: components/ui/* — 생성된 UI 라이브러리 컴포넌트]
- [예: 모든 타사 라이브러리 내부]

## 문서 동기화 유지

구현이 다음을 변경할 때마다 관련 컨텍스트 파일을 업데이트하세요:

- 시스템 아키텍처 또는 경계
- 저장소 모델 결정
- 코드 규칙 또는 표준
- 기능 범위

## 다음 단위로 이동하기 전에

1. 현재 단위가 정의된 범위 내에서 끝에서 끝까지 작동합니다
2. `architecture.md`에 정의된 불변성이 위반되지 않음
3. `progress-tracker.md`가 완료된 작업을 반영합니다
4. `npm run build`가 통과합니다

```

### context/architecture.md

```
# 아키텍처 컨텍스트

## 스택

| 레이어 | 기술 | 역할 |
| --------- | --------------------------- | ------ |
| 프레임워크 | [예: Next.js + TypeScript] | [역할] |
| UI | [예: Tailwind + shadcn/ui] | [역할] |
| 인증 | [예: Clerk] | [역할] |
| 데이터베이스 | [예: Prisma + PostgreSQL] | [역할] |
| [레이어] | [기술] | [역할] |

## 시스템 경계

- `[폴더]` — [이 폴더가 소유하고 책임지는 것]
- `[폴더]` — [이 폴더가 소유하고 책임지는 것]
- `[폴더]` — [이 폴더가 소유하고 책임지는 것]
- `[폴더]` — [이 폴더가 소유하고 책임지는 것]

## 저장소 모델

- **[저장소 유형 예: 데이터베이스]**: [여기에 있는 것 — 예: 메타데이터, 소유권, 관계]
- **[저장소 유형 예: Blob/파일 저장소]**: [여기에 있는 것 — 예: 생성된 파일, 미디어, 대용량 아티팩트]

## 인증 및 접근 제어 모델

- [인증 방식 — 예: 모든 사용자는 Clerk를 통해 로그인]
- [소유권 방식 — 예: 모든 프로젝트는 단일 소유자를 가짐]
- [접근 제어 방식 — 예: 소유자 또는 협력자만 프로젝트 리소스를 변경할 수 있음]

## 불변성

1. [코드베이스가 절대 위반해서는 안 되는 규칙 — 예: 요청 핸들러는 오래 지속되는 백그라운드 작업을 실행하지 않음]
2. [불변성 2]
3. [불변성 3]
4. [불변성 4]

```

### context/code-standards.md

```
# 코드 표준

## 일반

- [원칙 — 예: 모듈을 작고 단일 목적으로 유지]
- [원칙 — 예: 근본 원인을 해결하고 임시방편을 계층화하지 마세요]
- [원칙 — 예: 하나의 컴포넌트 또는 경로에서
  관련 없는 관심사를 섞지 마세요]

## TypeScript

- [규칙 — 예: 엄격 모드는 전체 프로젝트에 필요]
- [규칙 — 예: any를 피하세요 — 명시적 인터페이스 또는 좁은 범위의 타입 사용]
- [규칙 — 예: 시스템 경계에서 알려지지 않은 외부 입력을 신뢰하기 전에 검증]

## [프레임워크 — 예: Next.js]

- [규칙 — 예: 기본적으로 서버 컴포넌트 사용]
- [규칙 — 예: 브라우저 상호작용이 필요할 때만 use client 추가]
- [규칙 — 예: 경로 핸들러를 단일 책임에 집중된 상태로 유지]

## 스타일링

- [규칙 — 예: CSS 커스텀 프로퍼티 토큰 사용 — 하드코딩된 16진수 값 없음]
- [규칙 — 예: ui-context.md에 정의된 테두리 반경 스케일 따름]

## API 경로

- [규칙 — 예: 논리 실행 전에 요청 입력 검증 및 파싱]
- [규칙 — 예: 변경 전에 인증 및 소유권 시행]
- [규칙 — 예: 일관되고 예측 가능한 응답 형태 반환]

## 데이터 및 저장소

- [규칙 — 예: 메타데이터는 데이터베이스에]
- [규칙 — 예: 큰 생성된 콘텐츠는 파일 또는 blob 저장소에]
- [규칙 — 예: 큰 콘텐츠를 데이터베이스에 직접 저장하지 마세요]

## 파일 구성

- `[폴더]/` — [여기에 속하는 것]
- `[폴더]/` — [여기에 속하는 것]
- `[폴더]/` — [여기에 속하는 것]
- `[폴더]/` — [여기에 속하는 것]

```

### context/progress-tracker.md

```
# 진행 상황 추적

의미 있는 구현 변경 후마다
이 파일을 업데이트하세요.

## 현재 단계

- [예: 시작 전 / 진행 중 / 완료]

## 현재 목표

- [현재 빌드하고 있는 것]

## 완료된 작업

- 아직 없음.

## 진행 중

- 아직 없음.

## 다음

- [빌드할 첫 번째 단위]

## 미결 질문

- [해결되지 않은 제품 또는 기술 결정]

## 아키텍처 결정

- [시스템 설계 또는 데이터 모델에 영향을 미치는 결정 — 결정이 내려진 이유를 포함]

## 세션 메모

- [다음 세션에서 작업을 재개하기 위해 필요한 컨텍스트]

```

### context/project-overview.md

```
# [프로젝트 이름]

## 개요

[이 애플리케이션이 무엇을 하는지, 누구를 위한 것인지, 어떤 문제를 해결하는지 설명하는
한 문단.]

## 목표

1. [목표 1 — 구체적이고 측정 가능한]
2. [목표 2]
3. [목표 3]

## 핵심 사용자 흐름

1. [단계 1 — 예: 사용자가 로그인]
2. [단계 2]
3. [단계 3]
4. [핵심 흐름이 완료될 때까지 계속]

## 기능

### [기능 카테고리 1]

- [기능 설명]
- [기능 설명]

### [기능 카테고리 2]

- [기능 설명]
- [기능 설명]

## 범위

### 범위 내

- [빌드하고 있는 것]
- [빌드하고 있는 것]

### 범위 외

- [명시적으로 빌드하지 않는 것]
- [명시적으로 빌드하지 않는 것]

## 성공 기준

1. [구체적이고 검증 가능한 조건 — 예: 로그인한 사용자가 프로젝트를 생성하고 열 수 있음]
2. [조건 2]
3. [조건 3]

```

### context/ui-context.md

```
# UI 컨텍스트

## 테마

[전체 시각적 언어를 설명하세요 — 예: 다크 전용. 라이트 모드 없음. 디자인 언어는 다크 기술
작업공간 — 거의 검은 배경, 계층화된 서피스, 및 대화형 요소를 위한 생생한 액센트 색상.]

## 색상

[색상 토큰을 CSS 커스텀 프로퍼티로 정의하세요. 모든 컴포넌트는 이러한 토큰을 사용해야 합니다 — 하드코딩된 16진수 값은 없음.]

| 역할 | CSS 변수 | 값 |
| --------------- | ------------------ | -------- |
| 페이지 배경 | `--bg-base` | `#[hex]` |
| 서피스 | `--bg-surface` | `#[hex]` |
| 기본 텍스트 | `--text-primary` | `#[hex]` |
| 음수 텍스트 | `--text-muted` | `#[hex]` |
| 기본 액센트 | `--accent-primary` | `#[hex]` |
| 테두리 | `--border-default` | `#[hex]` |
| 오류 | `--state-error` | `#[hex]` |
| 성공 | `--state-success` | `#[hex]` |

## 타이포그래피

| 역할 | 폰트 | 변수 |
| --------- | ----------------- | ------------- |
| UI 텍스트 | [예: Geist Sans] | `--font-sans` |
| 코드/모노 | [예: Geist Mono] | `--font-mono` |

## 테두리 반경

| 컨텍스트 | 클래스 |
| ----------------- | ---------------- |
| 인라인 / 작은 UI | `rounded-[size]` |
| 카드 / 패널 | `rounded-[size]` |
| 모달 / 오버레이 | `rounded-[size]` |

## 컴포넌트 라이브러리

[예: Tailwind 위의 shadcn/ui. 컴포넌트는 components/ui/에 있습니다. 처음부터 작성하는 대신
CLI를 사용하여 새 컴포넌트를 추가하세요.]

## 레이아웃 패턴

- [패턴 — 예: 편집기: 왼쪽 사이드바, 중앙 캔버스, 오른쪽 사이드바가 있는 전체 뷰포트 분할]
- [패턴 — 예: 사이드바: 고정 너비와 테두리 구분자]
- [패턴 — 예: 모달: 배경 흐림이 있는 중앙 오버레이]
- [패턴 — 예: 네비게이션: 하단 테두리가 있는 상단 막대]

## 아이콘

[예: Lucide React. 스트로크 기반 아이콘만. 크기: 인라인의 경우 h-4 w-4, 버튼의 경우 h-5 w-5.]

```

