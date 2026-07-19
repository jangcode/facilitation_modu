<template>
  <div class="space-y-8">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 to-slate-900/90 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🧵 VIBE CODING PRACTICE PLAYBOOK
        </span>
        <h2 class="text-2xl sm:text-3xl font-black text-white tracking-tight mb-3">
          바이브 코딩 실습 가이드
        </h2>
        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed max-w-3xl">
          아이디어에서 작동하는 제품까지 빈 페이지에서 빠른 속도로 구현하는 **인공지능 주도 개발(AI-Driven Development) 플레이북**입니다. <br class="hidden sm:inline" />
          단순히 더 나은 프롬프트를 쓰는 기술을 넘어, 프롬프트를 보내기 전에 더 나은 사고를 하고 이를 에이전트와 동기화하는 구조화된 실습 가이드입니다.
        </p>
      </div>

      <!-- Live Color Dot Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Link</span>
      </div>
    </div>

    <!-- Inner Navigation Tabs -->
    <div class="flex flex-wrap gap-2 border-b border-slate-900 pb-3">
      <button
        v-for="tab in tabs"
        :key="tab.id"
        @click="activeTab = tab.id"
        class="px-4 py-2 rounded-xl text-xs font-bold transition-all flex items-center gap-2 border"
        :class="activeTab === tab.id
          ? 'bg-indigo-600/15 text-white border-indigo-500/40 shadow-sm'
          : 'bg-slate-900/40 text-slate-400 border-slate-800 hover:text-slate-300 hover:bg-slate-900'"
        :style="activeTab === tab.id ? { borderColor: stitchSettings.colorHex, color: stitchSettings.colorHex } : {}"
      >
        <span>{{ tab.icon }}</span>
        <span>{{ tab.name }}</span>
      </button>
    </div>

    <!-- Active Tab Content Area -->
    <div class="transition-all duration-300">

      <!-- Tab 1: Overview & Core Flow -->
      <div v-if="activeTab === 'intro'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('solid')">
          <h3 class="text-base font-extrabold text-white mb-3 flex items-center gap-2">
            💡 아이디어에서 제품까지: AI 기반 개발의 패러다임 쉬프트
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed mb-4">
            대부분의 개발자는 AI 코딩 도구를 열고 바로 코딩을 요청합니다. 이것은 분위기 코딩의 붕괴나 기능 표류(Feature Drift)로 이어지는 흔한 실수입니다.
            AI가 만들어내는 결과물의 품질은 당신이 AI에게 건네주는 <strong>'사고(Thinking)'의 품질</strong>로 결정됩니다. AI는 코드를 작성하는 강력한 조수일 뿐, 아키텍처적 설계와 비즈니스 목적을 정의하는 것은 당신의 몫입니다.
          </p>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-6">
            <div class="p-4 rounded-xl bg-slate-950/60 border border-red-500/20 text-xs">
              <h4 class="font-bold text-red-400 mb-2 flex items-center gap-1.5">
                ⚠️ 실패 유형 1: 분위기 코딩 붕괴 (Vibe Collapse)
              </h4>
              <p class="text-slate-400 leading-relaxed">
                넓고 모호하게 설명하여 처음 한 시간은 조립이 빠르지만, 기능을 덧붙일 때 이전에 결정했던 규칙들을 에이전트 스스로 모순되게 바꾸며 코드가 충돌하고 무너집니다. 토대가 없기 때문입니다.
              </p>
            </div>
            <div class="p-4 rounded-xl bg-slate-950/60 border border-yellow-500/20 text-xs">
              <h4 class="font-bold text-yellow-400 mb-2 flex items-center gap-1.5">
                ⚠️ 실패 유형 2: 기능 표류 (Feature Drift)
              </h4>
              <p class="text-slate-400 leading-relaxed">
                몇 주 뒤에 돌아와 새로운 기능을 추가하려 하면 에이전트가 이전의 아키텍처 결정, 네이밍 규칙, 특정 로직의 설계 의도를 잊어버리고 덮어써 버립니다. 세션 간 연속성이 없기 때문입니다.
              </p>
            </div>
          </div>
        </div>

        <!-- Core Commands Interface -->
        <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800">
          <h3 class="text-sm font-extrabold text-white mb-4 uppercase tracking-wider font-mono">
            ⚡ 실전 바이브 코딩 명령어 (Core Workflow Pattern)
          </h3>
          <p class="text-xs text-slate-400 mb-4">실용주의 바이브 코더들이 에이전트와 긴밀하게 소통할 때 사용하는 표준적인 4단계 제어 흐름입니다.</p>

          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 flex flex-col justify-between">
              <div>
                <span class="text-[10px] font-mono text-indigo-400 font-bold uppercase">Step 1</span>
                <h4 class="text-xs font-extrabold text-white font-mono mt-1 mb-2">/specify</h4>
                <p class="text-[11px] text-slate-500 leading-relaxed">구현하고자 하는 과제의 목표, 비즈니스 설명, 그리고 사용자 시나리오 및 핵심 기능들을 정의합니다.</p>
              </div>
            </div>

            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 flex flex-col justify-between">
              <div>
                <span class="text-[10px] font-mono text-pink-400 font-bold uppercase">Step 2</span>
                <h4 class="text-xs font-extrabold text-white font-mono mt-1 mb-2">/plan</h4>
                <p class="text-[11px] text-slate-500 leading-relaxed">분석을 진행하고, 소프트웨어 구조(아키텍처), 스택, 데이터 흐름, API 구조 및 릴리즈 전략을 세웁니다.</p>
              </div>
            </div>

            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 flex flex-col justify-between">
              <div>
                <span class="text-[10px] font-mono text-emerald-400 font-bold uppercase">Step 3</span>
                <h4 class="text-xs font-extrabold text-white font-mono mt-1 mb-2">/tasks</h4>
                <p class="text-[11px] text-slate-500 leading-relaxed">전체 목표를 즉시 실행 가능하고 독립적인 크기의 작은 빌드 단위(Unit)로 쪼개고 목록화합니다.</p>
              </div>
            </div>

            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 flex flex-col justify-between">
              <div>
                <span class="text-[10px] font-mono text-amber-400 font-bold uppercase">Step 4</span>
                <h4 class="text-xs font-extrabold text-white font-mono mt-1 mb-2">/implement</h4>
                <p class="text-[11px] text-slate-500 leading-relaxed">각 단위(Unit)별로 스펙 사양서에 부합하는 코드를 자가 수정과 로컬 테스트를 거치며 점진적으로 완성해 나갑니다.</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Tab 2: Before Building Planning -->
      <div v-if="activeTab === 'planning'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('dashed')">
          <h3 class="text-base font-extrabold text-white mb-2 flex items-center gap-2">
            🌱 1단계: 코드 한 줄 쓰기 전에, 설계자(Architect)가 되세요
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed mb-4">
            에이전트가 코드에 손대기 전에 시스템을 머릿속에 설계하고, 규칙을 명확히 정의하는 일종의 **"인간-AI 예비 대화"** 세션이 필수적입니다.
            Claude, ChatGPT 등 범용 AI 도구를 열고 아이디어를 다듬기 위해 아래 프롬프트를 복사하여 대화를 시작해 보세요.
          </p>

          <!-- Interactive Prompt Area -->
          <div class="bg-slate-950 p-4 rounded-xl border border-slate-800 space-y-3 relative">
            <div class="flex items-center justify-between">
              <span class="text-[11px] font-mono text-slate-500 font-semibold uppercase">📋 AI 기획 협업용 프롬프트</span>
              <button
                @click="copyText(planningPrompt)"
                class="px-2.5 py-1 rounded bg-slate-900 hover:bg-slate-800 border border-slate-800 hover:border-slate-700 text-[10px] text-slate-300 font-bold transition-all"
              >
                {{ copyStatus.planning ? '복사 완료! 👍' : '클립보드 복사' }}
              </button>
            </div>
            <pre class="text-[11px] font-mono text-slate-300 bg-slate-950 p-3 rounded border border-slate-900 overflow-x-auto whitespace-pre-wrap leading-relaxed max-h-64">{{ planningPrompt }}</pre>
          </div>
        </div>

        <!-- Essential Questions Callout -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="p-5 rounded-2xl bg-slate-900/30 border border-slate-800">
            <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-3 text-indigo-400">🎁 제품 측면의 질문</h4>
            <ul class="space-y-2 text-[11px] text-slate-400 leading-relaxed list-disc pl-4">
              <li>이 애플리케이션은 한 문장으로 무엇을 하는가?</li>
              <li>주요 사용자는 누구이며 핵심 가치는 무엇인가?</li>
              <li>회원가입 후 핵심 가치에 도달하는 유저 플로우는?</li>
              <li>첫 버전의 가장 중요한 3대 기능은 무엇인가?</li>
              <li>의도적으로 범위에서 제외시킬 것은 무엇인가?</li>
            </ul>
          </div>

          <div class="p-5 rounded-2xl bg-slate-900/30 border border-slate-800">
            <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-3 text-pink-400">⚙️ 기술 및 불변조건</h4>
            <ul class="space-y-2 text-[11px] text-slate-400 leading-relaxed list-disc pl-4">
              <li>전체 기술 스택과 라이브러리를 왜 선택했는가?</li>
              <li>데이터는 어디에 저장되는가 (DB, 파일, 캐시)?</li>
              <li>사용자 인증 및 리소스 소유권 검증 모델은?</li>
              <li>구조적 폴더 경계와 각 폴더의 역할은?</li>
              <li>코드베이스가 **절대 위반해서는 안 되는 규칙**은?</li>
            </ul>
          </div>

          <div class="p-5 rounded-2xl bg-slate-900/30 border border-slate-800">
            <h4 class="text-xs font-bold text-white uppercase tracking-wider mb-3 text-amber-400">🎨 디자인 & UI 표준</h4>
            <ul class="space-y-2 text-[11px] text-slate-400 leading-relaxed list-disc pl-4">
              <li>메인 색상 팔레트와 디자인 토큰은 무엇인가?</li>
              <li>사용할 UI 컴포넌트와 아이콘 라이브러리는?</li>
              <li>기본이 되는 레이아웃 패턴(사이드바, 네비게이션)은?</li>
              <li>테두리 곡률 및 스티치 디테일은 어떻게 제어하는가?</li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Tab 3: 6 Context Templates -->
      <div v-if="activeTab === 'context'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('double')">
          <h3 class="text-base font-extrabold text-white mb-2 flex items-center gap-2">
            📂 2단계: 6대 컨텍스트 파일 패턴 (Context Memory Bank)
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed">
            AI 에이전트는 세션 간 연속적인 메모리가 없으므로, 프로젝트 루트의 <strong>Memory Bank</strong>를 읽고 컨텍스트를 회복하도록 해야 합니다.
            이 6개의 파일을 루트 `context/` 폴더에 배치하고 진입점으로 `AGENTS.md`(또는 `CLAUDE.md`)를 두어 에이전트가 작업을 시작하기 전 무조건 읽게 만드세요.
          </p>
        </div>

        <!-- Split View: File Selector + Preview template -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">

          <!-- Left Selector -->
          <div class="lg:col-span-1 space-y-2">
            <button
              v-for="file in contextFiles"
              :key="file.name"
              @click="selectedContextFile = file"
              class="w-full text-left p-3.5 rounded-xl border text-xs flex items-center justify-between transition-all"
              :class="selectedContextFile.name === file.name
                ? 'bg-slate-950 border-indigo-500/50 text-white font-bold'
                : 'bg-slate-900/30 border-slate-800 hover:border-slate-700 text-slate-400'"
              :style="selectedContextFile.name === file.name ? { borderLeftWidth: '4px', borderLeftColor: stitchSettings.colorHex } : {}"
            >
              <div class="flex flex-col">
                <span class="font-mono text-[10px] text-slate-500 uppercase">{{ file.title }}</span>
                <span class="font-mono mt-0.5">{{ file.name }}</span>
              </div>
              <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-slate-500">
                <polyline points="9 18 15 12 9 6"/>
              </svg>
            </button>
          </div>

          <!-- Right Code Viewer -->
          <div class="lg:col-span-2 space-y-3">
            <div class="bg-slate-900/80 p-5 rounded-2xl border border-slate-800 space-y-3">
              <div class="flex items-center justify-between">
                <div>
                  <h4 class="text-xs font-bold text-white font-mono">{{ selectedContextFile.name }}</h4>
                  <p class="text-[10px] text-slate-500 mt-0.5">{{ selectedContextFile.desc }}</p>
                </div>
                <button
                  @click="copyText(selectedContextFile.template, 'selectedContext')"
                  class="px-2.5 py-1 rounded bg-slate-950 hover:bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-bold transition-all"
                >
                  {{ copyStatus.selectedContext ? '복사 완료!' : '템플릿 복사' }}
                </button>
              </div>

              <div class="bg-slate-950 rounded-xl p-4 border border-slate-900 font-mono text-[11px] leading-relaxed text-slate-300 overflow-y-auto max-h-[380px] whitespace-pre">
                {{ selectedContextFile.template }}
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Tab 4: Spec Breakdown -->
      <div v-if="activeTab === 'spec'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('dotted')">
          <h3 class="text-base font-extrabold text-white mb-2 flex items-center gap-2">
            🎯 3단계: 빌드 분해 & 스펙 기반 개발 (Spec-Driven Development)
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed mb-4">
            모든 기능은 에이전트가 손대기 전에 명확하고 검증 가능한 종료 상태를 가져야 합니다.
            전체 비즈니스 요구사항을 '독립된 빌드 단위(Unit)'로 조각낸 뒤, 각 단위마다 개별 스펙 문서를 작성하세요.
          </p>

          <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mt-4">
            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 text-xs">
              <h4 class="font-bold text-white mb-1.5">1. 의존성 역전 우선</h4>
              <p class="text-slate-500 leading-relaxed">A 기능을 빌드하기 위해 B 기능이 필요하다면 A를 만들기 전 B를 먼저 완성합니다.</p>
            </div>
            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 text-xs">
              <h4 class="font-bold text-white mb-1.5">2. 보안 우선</h4>
              <p class="text-slate-500 leading-relaxed">인증과 데이터 접근 제어 규칙을 화면 UI나 추가적인 비즈니스 로직보다 선행하여 배치합니다.</p>
            </div>
            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 text-xs">
              <h4 class="font-bold text-white mb-1.5">3. 백엔드 전용 API 먼저</h4>
              <p class="text-slate-500 leading-relaxed">API 엔드포인트를 완전히 구현한 후, 다음 작업 단위에서 UI를 통합해 충돌 여지를 줄입니다.</p>
            </div>
            <div class="bg-slate-950 p-4 rounded-xl border border-slate-900 text-xs">
              <h4 class="font-bold text-white mb-1.5">4. UI 뼈대 & 모의 데이터</h4>
              <p class="text-slate-500 leading-relaxed">정적 목업 데이터를 사용해 UI 컴포넌트를 우선 렌더링하고 나중에 실제 API 호출을 엮습니다.</p>
            </div>
          </div>
        </div>

        <!-- Spec Template Card -->
        <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800 space-y-4">
          <div class="flex items-center justify-between">
            <h4 class="text-xs font-bold text-white uppercase tracking-wider font-mono">📝 단위별 개별 스펙 템플릿 (Spec Template)</h4>
            <button
              @click="copyText(specTemplate, 'spec')"
              class="px-2.5 py-1 rounded bg-slate-950 hover:bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-bold transition-all"
            >
              {{ copyStatus.spec ? '복사 완료!' : '템플릿 복사' }}
            </button>
          </div>
          <pre class="text-[11px] font-mono text-slate-300 bg-slate-950 p-4 rounded-xl border border-slate-900 overflow-x-auto whitespace-pre leading-relaxed max-h-80">{{ specTemplate }}</pre>
        </div>
      </div>

      <!-- Tab 5: Practical Workflow -->
      <div v-if="activeTab === 'workflow'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('dashed')">
          <h3 class="text-base font-extrabold text-white mb-2 flex items-center gap-2">
            🚀 4단계: 에이전트와 교류하는 3-프롬프트 루프 (3-Prompt Workflow)
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed mb-4">
            스펙 문서와 기획이 끝났다면 실제 구현 세션을 열고 아래와 같이 매우 정밀하게 설계된 세 단계의 조율 명령어를 통해 완벽한 품질을 유지해 나가세요.
          </p>

          <div class="space-y-4">
            <!-- Step 1 Prompt -->
            <div class="p-4 rounded-xl bg-slate-950/60 border border-slate-800 space-y-2">
              <div class="flex items-center justify-between">
                <span class="inline-flex items-center gap-1.5 px-2 py-0.5 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-[10px] font-bold">
                  Prompt 1. 구현 실행 명령
                </span>
                <button
                  @click="copyText(p1Code, 'p1')"
                  class="px-2 py-0.5 rounded bg-slate-900 hover:bg-slate-800 border border-slate-800 text-[9px] text-slate-300 transition-all"
                >
                  {{ copyStatus.p1 ? '복사 완료!' : '복사' }}
                </button>
              </div>
              <pre class="text-[11px] font-mono text-slate-300 bg-slate-950 p-2.5 rounded border border-slate-900 overflow-x-auto whitespace-pre-wrap leading-relaxed">{{ p1Code }}</pre>
            </div>

            <!-- Step 2 Prompt -->
            <div class="p-4 rounded-xl bg-slate-950/60 border border-slate-800 space-y-2">
              <div class="flex items-center justify-between">
                <span class="inline-flex items-center gap-1.5 px-2 py-0.5 rounded-full bg-pink-500/10 border border-pink-500/20 text-pink-300 text-[10px] font-bold">
                  Prompt 2. 편차 수정 및 자가 치유
                </span>
                <button
                  @click="copyText(p2Code, 'p2')"
                  class="px-2 py-0.5 rounded bg-slate-900 hover:bg-slate-800 border border-slate-800 text-[9px] text-slate-300 transition-all"
                >
                  {{ copyStatus.p2 ? '복사 완료!' : '복사' }}
                </button>
              </div>
              <pre class="text-[11px] font-mono text-slate-300 bg-slate-950 p-2.5 rounded border border-slate-900 overflow-x-auto whitespace-pre-wrap leading-relaxed">{{ p2Code }}</pre>
            </div>

            <!-- Step 3 Prompt -->
            <div class="p-4 rounded-xl bg-slate-950/60 border border-slate-800 space-y-2">
              <div class="flex items-center justify-between">
                <span class="inline-flex items-center gap-1.5 px-2 py-0.5 rounded-full bg-emerald-500/10 border border-emerald-500/20 text-emerald-300 text-[10px] font-bold">
                  Prompt 3. 세션 종료 및 완료 기록
                </span>
                <button
                  @click="copyText(p3Code, 'p3')"
                  class="px-2 py-0.5 rounded bg-slate-900 hover:bg-slate-800 border border-slate-800 text-[9px] text-slate-300 transition-all"
                >
                  {{ copyStatus.p3 ? '복사 완료!' : '복사' }}
                </button>
              </div>
              <pre class="text-[11px] font-mono text-slate-300 bg-slate-950 p-2.5 rounded border border-slate-900 overflow-x-auto whitespace-pre-wrap leading-relaxed">{{ p3Code }}</pre>
            </div>
          </div>
        </div>
      </div>

      <!-- Tab 6: Interactive Practice Checklist -->
      <div v-if="activeTab === 'checklist'" class="space-y-6">
        <div class="bg-slate-900/50 p-6 rounded-2xl border" :style="getStitchStyle('solid')">
          <h3 class="text-base font-extrabold text-white mb-2 flex items-center gap-2">
            ✅ 실시간 바이브 코딩 실습 체크리스트 (Self-Verification Panel)
          </h3>
          <p class="text-xs text-slate-400 leading-relaxed mb-4">
            당신이 기획한 프로젝트를 에이전트와 함께 완주하기까지의 점검 요소들을 하나씩 체크하며 온전한 흐름을 유지하고 있는지 실시간 확인해 보세요.
          </p>

          <!-- Checklist grid -->
          <div class="space-y-3">
            <div
              v-for="(item, index) in checklistItems"
              :key="index"
              class="p-4 rounded-xl bg-slate-950/80 border border-slate-800 hover:border-slate-700 transition-all flex items-start gap-3.5 cursor-pointer"
              @click="toggleChecklist(index)"
            >
              <div class="mt-0.5 flex-shrink-0">
                <div
                  class="w-5 h-5 rounded border flex items-center justify-center transition-all"
                  :class="item.checked ? 'bg-indigo-600 border-indigo-500 text-white' : 'border-slate-700 bg-slate-900'"
                  :style="item.checked ? { backgroundColor: stitchSettings.colorHex, borderColor: stitchSettings.colorHex } : {}"
                >
                  <svg v-if="item.checked" xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </div>
              </div>
              <div>
                <h4 class="text-xs font-bold text-white flex items-center gap-2">
                  <span class="text-[10px] font-mono text-indigo-400 font-semibold" :style="{ color: item.checked ? stitchSettings.colorHex : '' }">[{{ item.phase }}]</span>
                  <span :class="{ 'line-through text-slate-500': item.checked }">{{ item.text }}</span>
                </h4>
                <p class="text-[11px] text-slate-500 mt-1 leading-relaxed">{{ item.description }}</p>
              </div>
            </div>
          </div>

          <!-- Progress Bar -->
          <div class="pt-4 border-t border-slate-900/80 mt-6 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
            <div class="flex items-center gap-2">
              <span class="text-xs font-bold text-white">가이드 이수율:</span>
              <span class="text-xs font-mono font-black" :style="{ color: stitchSettings.colorHex }">{{ progressPercentage }}%</span>
              <span class="text-[10px] text-slate-500">({{ checkedCount }} / {{ checklistItems.length }} 완료)</span>
            </div>
            <div class="flex-grow max-w-xs h-2 bg-slate-950 rounded-full overflow-hidden border border-slate-900">
              <div
                class="h-full transition-all duration-500"
                :style="{ width: `${progressPercentage}%`, backgroundColor: stitchSettings.colorHex }"
              ></div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'VibeCodingGuide',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const activeTab = ref('intro')

    const tabs = [
      { id: 'intro', name: '가이드 개요', icon: '📖' },
      { id: 'planning', name: '빌드 전 기획', icon: '💭' },
      { id: 'context', name: '6대 컨텍스트 설계', icon: '📁' },
      { id: 'spec', name: '작업 단위 세분화', icon: '🎯' },
      { id: 'workflow', name: '실전 워크플로우', icon: '⚡' },
      { id: 'checklist', name: '자가 실습 진단', icon: '✅' }
    ]

    // Clipboards copy handles
    const copyStatus = ref({
      planning: false,
      selectedContext: false,
      spec: false,
      p1: false,
      p2: false,
      p3: false
    })

    const copyText = (text, type = 'planning') => {
      navigator.clipboard.writeText(text).then(() => {
        copyStatus.value[type] = true
        setTimeout(() => {
          copyStatus.value[type] = false
        }, 2000)
      }).catch(err => {
        console.error('Copy failed:', err)
      })
    }

    // Prompts content
    const planningPrompt = `애플리케이션에 대한 아이디어가 있습니다.
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
코드를 작성하기 전에 시스템에 대해 명확하게 생각할 수 있도록 도와주세요.`

    const p1Code = `Read context/specs/NN-feature-name.md.
Update context/progress-tracker.md to mark this as in progress.
Implement it exactly as specified.
Do not go beyond the scope of this unit.`

    const p2Code = `The [specific element] does not match the spec.
Expected: [what the spec says].
Current: [what was built].
Fix only this. Do not change anything else.`

    const p3Code = `Implementation is complete and verified.
Mark unit NN complete in context/progress-tracker.md.
Push branch feat/NN-feature-name to GitHub.`

    const specTemplate = `# Unit NN: [Feature Name]

## Goal
One or two sentences describing the concrete output of this unit.

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
- [ ] npm run build passes`

    // Context Files Mock Data
    const contextFiles = [
      {
        title: 'Application Root Entry',
        name: 'AGENTS.md / CLAUDE.md',
        desc: '에이전트가 동작하기 전에 무조건 참조해야 하는 첫 진입 경로입니다.',
        template: `## Application Building Context

Read the following files in order before implementing or making any architectural decision:

1. \`context/project-overview.md\` — product definition, goals, features, and scope
2. \`context/architecture.md\` — system structure, boundaries, storage model, and invariants
3. \`context/ui-context.md\` — theme, colors, typography, and component conventions
4. \`context/code-standards.md\` — implementation rules and conventions
5. \`context/ai-workflow-rules.md\` — development workflow, scoping rules, and delivery approach
6. \`context/progress-tracker.md\` — current phase, completed work, open questions, and next steps

Update \`context/progress-tracker.md\` after each meaningful implementation change.

If implementation changes the architecture, scope, or standards documented in the context files, update the relevant file before continuing.`
      },
      {
        title: 'Project Overview',
        name: 'project-overview.md',
        desc: '프로젝트가 풀고자 하는 목표, 핵심 기능 및 명확한 범위(In & Out) 정의',
        template: `# [프로젝트 이름]

## 개요
[이 애플리케이션이 무엇을 하는지, 누구를 위한 것인지, 어떤 문제를 해결하는지 설명하는 한 문단.]

## 목표
1. [목표 1 — 구체적이고 측정 가능한]
2. [목표 2]
3. [목표 3]

## 핵심 사용자 흐름
1. [단계 1 — 예: 사용자가 로그인]
2. [단계 2]
3. [단계 3]

## 기능
### [기능 카테고리 1]
- [기능 설명]
- [기능 설명]

## 범위
### 범위 내
- [빌드하고 있는 것]
### 범위 외
- [명시적으로 빌드하지 않는 것]

## 성공 기준
1. [구체적이고 검증 가능한 조건 — 예: 로그인한 사용자가 프로젝트를 생성하고 열 수 있음]
2. [조건 2]`
      },
      {
        title: 'System Architecture',
        name: 'architecture.md',
        desc: '기술 스택, 시스템 책임 폴더 경계, 데이터 보관 위치 및 결코 위반 금지인 4대 불변 법칙',
        template: `# 아키텍처 컨텍스트

## 스택
| 레이어 | 기술 | 역할 |
| --------- | --------------------------- | ------ |
| 프레임워크 | [예: Next.js + TypeScript] | [역할] |
| UI | [예: Tailwind + shadcn/ui] | [역할] |

## 시스템 경계
- \`[폴더]\` — [이 폴더가 소유하고 책임지는 것]
- \`[폴더]\` — [이 폴더가 소유하고 책임지는 것]

## 저장소 모델
- **[저장소 유형 예: 데이터베이스]**: [여기에 있는 것 — 예: 메타데이터, 소유권, 관계]

## 인증 및 접근 제어 모델
- [인증 방식 — 예: 모든 사용자는 Clerk를 통해 로그인]
- [소유권 방식 — 예: 모든 프로젝트는 단일 소유자를 가짐]

## 불변성
1. [코드베이스가 절대 위반해서는 안 되는 규칙 — 예: 요청 핸들러는 오래 지속되는 백그라운드 작업을 실행하지 않음]
2. [불변성 2]
3. [불변성 3]
4. [불변성 4]`
      },
      {
        title: 'Workflow Rules',
        name: 'ai-workflow-rules.md',
        desc: '에이전트가 어떤 범위 규율을 준수하며, 결정을 유보하고 질문할지 지시하는 명령형 지침',
        template: `# AI 워크플로우 규칙

## 접근 방식
[사양 기반 워크플로우를 사용하여 이 프로젝트를 점진적으로 빌드합니다. 항상 사양에 따라 구현하며, 결정을 마음대로 발명하지 마세요.]

## 범위 규칙
- 한 번에 하나의 기능 단위에 대해 작업
- 큰 추측성 변경보다 작고 검증 가능한 증분 선호

## 작업을 분할할 시기
변경을 빠르게 끝에서 끝까지 검증할 수 없으면, 범위가 너무 넓습니다 — 분할하세요.

## 누락된 요구사항 처리
- 요구사항이 모호하면, 구현하기 전에 관련 컨텍스트 파일에서 해결하세요
- 요구사항이 누락되면, 계속하기 전에 \`progress-tracker.md\`에 미결 질문으로 추가하세요

## 보호된 파일
명시적으로 지시되지 않는 한 다음을 수정하지 마세요:
- [예: components/ui/* — 생성된 UI 라이브러리 컴포넌트]

## 문서 동기화 유지
구현이 설계 사항을 변경할 때마다 관련 컨텍스트 파일을 업데이트하세요.`
      },
      {
        title: 'UI Context Specs',
        name: 'ui-context.md',
        desc: '디자인 시스템, 시각적 언어 토큰, 여백 및 아이콘 설정 파일',
        template: `# UI 컨텍스트

## 테마
[디자인 언어는 다크 기술 작업공간 — 거의 검은 배경, 계층화된 서피스, 및 대화형 요소를 위한 생생한 액센트 색상.]

## 색상
| 역할 | CSS 변수 | 값 |
| --------------- | ------------------ | -------- |
| 페이지 배경 | \`--bg-base\` | \`#[hex]\` |
| 서피스 | \`--bg-surface\` | \`#[hex]\` |
| 기본 텍스트 | \`--text-primary\` | \`#[hex]\` |

## 타이포그래피
| 역할 | 폰트 | 변수 |
| --------- | ----------------- | ------------- |
| UI 텍스트 | [예: Geist Sans] | \`--font-sans\` |

## 레이아웃 패턴
- [패턴 — 예: 사이드바: 고정 너비와 테두리 구분자]`
      },
      {
        title: 'Code Standards',
        name: 'code-standards.md',
        desc: 'TypeScript 코딩 규칙, 라우트 규격 및 리팩토링 기대 사양',
        template: `# 코드 표준

## 일반
- [원칙 — 예: 모듈을 작고 단일 목적으로 유지]
- [원칙 — 예: 하나의 컴포넌트 또는 경로에서 관련 없는 관심사를 섞지 마세요]

## TypeScript
- [규칙 — 예: any를 피하세요 — 명시적 인터페이스 또는 좁은 범위의 타입 사용]

## 파일 구성
- \`[폴더]/\` — [여기에 속하는 것]`
      },
      {
        title: 'Progress Tracker',
        name: 'progress-tracker.md',
        desc: '현재의 랜드마크, 완료 완료 항목 및 다음 단위로의 핸드오프를 매 세션 기록하는 유일한 유동 파일',
        template: `# 진행 상황 추적

Update this file after every meaningful implementation change.

## Current Phase
- [예: 시작 전 / 진행 중 / 완료]

## Current Goal
- [현재 빌드하고 있는 것]

## Completed
- 아직 없음.

## In Progress
- 아직 없음.

## Next Up
- [빌드할 첫 번째 단위]

## Open Questions
- [해결되지 않은 제품 또는 기술 결정]

## Session Notes
- [다음 세션에서 작업을 재개하기 위해 필요한 컨텍스트]`
      }
    ]

    const selectedContextFile = ref(contextFiles[0])

    // Self-verification checklist data
    const checklistItems = ref([
      { phase: '기획', text: '기획용 대화 프롬프트를 AI 에이전트에 질의하여 모호함 제거하기', description: '기능의 범위와 기술 제약조건을 사전에 완전히 정의하고, "내가 이미 아키텍처링한 것을 AI가 수행"하도록 준비했는지 점검합니다.', checked: false },
      { phase: '환경', text: '루트 경로에 Memory Entry (AGENTS.md 등) 생성하기', description: 'AI 에이전트가 리포지토리 로딩 시 최우선적으로 읽을 가이드라인 체계를 셋업했는지 확인합니다.', checked: false },
      { phase: '설계', text: 'context/ 폴더 내에 6대 컨텍스트 뼈대 작성하기', description: 'Project Overview, Architecture, Code Standards, UI Context, Workflows, Progress Tracker 6개 파일을 구성하였는지 확인합니다.', checked: false },
      { phase: '분해', text: '빌드 플랜(00-build-plan.md) 구성하기', description: '어떤 기능이든 15분~1시간 내외에 빌드가 가능한 수준의 작업 단위(Unit)로 명확한 종속성에 맞춰 정렬했는지 확인합니다.', checked: false },
      { phase: '수행', text: '개별 스펙 가이드를 읽히는 First Prompt 사용하기', description: 'AI에게 스펙만을 정확하게 읽히고 그 범위를 초과하는 추측성 오염이 없도록 제어하는 3-프롬프트 루프를 준수했는지 확인합니다.', checked: false },
      { phase: '완료', text: 'npm run build를 통해 프로덕션 검증 완료하기', description: '작업 단위가 완료될 때마다 로컬 테스트와 빌드를 수행하고, Progress Tracker를 꼼꼼하게 업데이트하여 세션 연속성을 확보했는지 점검합니다.', checked: false }
    ])

    const toggleChecklist = (index) => {
      checklistItems.value[index].checked = !checklistItems.value[index].checked
    }

    const checkedCount = computed(() => {
      return checklistItems.value.filter(item => item.checked).length
    })

    const progressPercentage = computed(() => {
      if (checklistItems.value.length === 0) return 0
      return Math.round((checkedCount.value / checklistItems.value.length) * 100)
    })

    // Stitch responsive decorators
    const customStitchLineStyle = computed(() => {
      const color = props.stitchSettings.colorHex || '#ec4899'
      const gap = props.stitchSettings.gap || 8
      const style = props.stitchSettings.style || 'dashed'

      if (style === 'solid') {
        return { backgroundColor: color }
      }

      return {
        backgroundImage: `linear-gradient(90deg, ${color} 50%, transparent 50%)`,
        backgroundSize: `${gap * 2}px 100%`,
        height: `${props.stitchSettings.thickness || 2}px`
      }
    })

    const getStitchStyle = (styleType) => {
      const color = props.stitchSettings.colorHex || '#ec4899'
      const thick = `${props.stitchSettings.thickness || 2}px`
      let borderStyle = styleType

      return {
        borderWidth: thick,
        borderColor: color,
        borderStyle: borderStyle,
        boxShadow: `0 4px 15px rgba(0,0,0,0.1), 0 0 10px ${color}10`
      }
    }

    return {
      activeTab,
      tabs,
      copyStatus,
      copyText,
      planningPrompt,
      p1Code,
      p2Code,
      p3Code,
      specTemplate,
      contextFiles,
      selectedContextFile,
      checklistItems,
      toggleChecklist,
      checkedCount,
      progressPercentage,
      customStitchLineStyle,
      getStitchStyle
    }
  }
}
</script>
