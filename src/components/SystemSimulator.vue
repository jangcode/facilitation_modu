<template>
  <div class="space-y-12">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 via-slate-900/90 to-slate-950 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🌐 WEB ARCHITECTURE INTERACTIVE SIMULATOR
        </span>
        <h2 class="text-2xl sm:text-4xl font-black text-white tracking-tight mb-3">
          웹 서비스 아키텍처 워크플로우 시뮬레이션
        </h2>
        <p class="text-base text-slate-400 leading-relaxed max-w-3xl">
          웹 서비스의 핵심 4단계 계층인 <strong class="text-indigo-300 font-semibold">사용자(User) ➔ 프론트엔드(Frontend) ➔ 백엔드(Backend) ➔ 데이터베이스(Database)</strong> 간의 유기적인 통신 흐름과, 각 계층에서의 <strong class="text-amber-300 font-semibold">하드웨어(HW)</strong>와 <strong class="text-emerald-300 font-semibold">소프트웨어(SW)</strong> 역할을 실시간으로 시뮬레이션합니다.
        </p>
      </div>

      <!-- Live Stitch Color Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2 hidden sm:flex">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Architecture</span>
      </div>
    </div>

    <!-- HW vs SW Classification 4-Layer Matrix -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h3 class="text-xl font-black text-white">4계층 아키텍처: HW (하드웨어) vs SW (소프트웨어) 역할 구분</h3>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        웹 서비스를 구성하는 물리적 기기 및 설비인 <strong class="text-amber-400">하드웨어(HW)</strong>와, 그 위에서 작동하는 데이터 처리 및 프로그램 로직인 <strong class="text-emerald-400">소프트웨어(SW)</strong>를 구분하여 이해할 수 있습니다.
      </p>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 pt-2">
        <!-- 1. User Layer -->
        <div class="bg-slate-900/60 p-5 rounded-2xl border border-slate-800 space-y-4 flex flex-col justify-between">
          <div>
            <div class="flex items-center justify-between mb-2">
              <span class="text-xs font-mono font-bold text-blue-400 uppercase tracking-wider">01. USER</span>
              <span class="px-2 py-0.5 rounded bg-blue-500/10 text-blue-300 border border-blue-500/20 text-[10px] font-bold">Client Device</span>
            </div>
            <h4 class="text-base font-extrabold text-white mb-3">👤 사용자 (User)</h4>

            <div class="space-y-3 text-base">
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>🔧 HW (하드웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  스마트폰, PC, 마우스/키보드 입력기기, OLED/LCD 디스플레이, RAM, Wi-Fi/NIC 모듈
                </p>
              </div>
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>💻 SW (소프트웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  OS(iOS, Android, Windows), 웹 브라우저(Chrome, Safari), 사용자 터치/클릭 이벤트 핸들러
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- 2. Frontend Layer -->
        <div class="bg-slate-900/60 p-5 rounded-2xl border border-slate-800 space-y-4 flex flex-col justify-between">
          <div>
            <div class="flex items-center justify-between mb-2">
              <span class="text-xs font-mono font-bold text-cyan-400 uppercase tracking-wider">02. FRONTEND</span>
              <span class="px-2 py-0.5 rounded bg-cyan-500/10 text-cyan-300 border border-cyan-500/20 text-[10px] font-bold">Client App / CDN</span>
            </div>
            <h4 class="text-base font-extrabold text-white mb-3">💻 프론트엔드 (Frontend)</h4>

            <div class="space-y-3 text-base">
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>🔧 HW (하드웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  CDN 엣지 서버 HW, 브라우저 GPU(화면 렌더링 파이프라인), CPU 렌더링 코어
                </p>
              </div>
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>💻 SW (소프트웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  Vue.js / React, HTML5 DOM, CSS Tailwind, V8 JS 엔진, Fetch / Axios HTTP 클라이언트
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- 3. Backend Layer -->
        <div class="bg-slate-900/60 p-5 rounded-2xl border border-slate-800 space-y-4 flex flex-col justify-between">
          <div>
            <div class="flex items-center justify-between mb-2">
              <span class="text-xs font-mono font-bold text-purple-400 uppercase tracking-wider">03. BACKEND</span>
              <span class="px-2 py-0.5 rounded bg-purple-500/10 text-purple-300 border border-purple-500/20 text-[10px] font-bold">App Server</span>
            </div>
            <h4 class="text-base font-extrabold text-white mb-3">⚙️ 백엔드 (Backend)</h4>

            <div class="space-y-3 text-base">
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>🔧 HW (하드웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  클라우드 EC2/호스트 랙 서버, 수십코어 CPU 프로세서, 서버 RAM, 데이터센터 로드밸런서
                </p>
              </div>
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>💻 SW (소프트웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  Node.js, Express, Spring Boot, Nginx, REST API 라우터, JWT 인증 미들웨어, ORM
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- 4. Database Layer -->
        <div class="bg-slate-900/60 p-5 rounded-2xl border border-slate-800 space-y-4 flex flex-col justify-between">
          <div>
            <div class="flex items-center justify-between mb-2">
              <span class="text-xs font-mono font-bold text-emerald-400 uppercase tracking-wider">04. DATABASE</span>
              <span class="px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-300 border border-emerald-500/20 text-[10px] font-bold">Data Storage</span>
            </div>
            <h4 class="text-base font-extrabold text-white mb-3">🗄️ 데이터베이스 (Database)</h4>

            <div class="space-y-3 text-base">
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>🔧 HW (하드웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  고성능 NVMe SSD 스토리지 RAID 배열, ECC 메모리 버퍼, 백업 전용 스토리지 HW
                </p>
              </div>
              <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
                <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                  <span>💻 SW (소프트웨어)</span>
                </div>
                <p class="text-base text-slate-300 leading-relaxed">
                  PostgreSQL, MySQL, DBMS Query Engine, B-Tree 인덱서, 트랜잭션 (ACID) 로그 엔진
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Interactive Workflow Simulation Playground -->
    <section class="space-y-6">
      <div class="flex flex-col md:flex-row md:items-center justify-between border-b border-slate-900 pb-4 gap-4">
        <div class="flex items-center gap-2">
          <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
          <div>
            <h3 class="text-xl font-black text-white">시나리오 기반 인터랙티브 패킷 흐름 시뮬레이터</h3>
            <p class="text-xs text-slate-400">시나리오를 선택하고 [자동 실행] 또는 [다음 단계]를 눌러 데이터 전송 과정을 직접 확인하세요.</p>
          </div>
        </div>

        <!-- Scenario Selector Dropdown -->
        <div class="flex items-center gap-2">
          <label class="text-xs font-bold text-slate-400 whitespace-nowrap">시나리오 선택:</label>
          <select
            v-model="selectedScenarioKey"
            @change="onScenarioChange"
            class="bg-slate-900 border border-slate-700 text-indigo-300 font-bold text-xs rounded-xl px-3 py-2 outline-none focus:border-indigo-500 transition-all cursor-pointer"
          >
            <option value="search">🔍 [GET] 상품/데이터 조회 요청</option>
            <option value="auth">🔐 [POST] 회원가입 및 로그인 처리</option>
            <option value="create">📝 [POST] 게시글/데이터 작성 및 저장</option>
          </select>
        </div>
      </div>

      <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 sm:p-8 relative overflow-hidden space-y-8">

        <!-- Top Control Bar -->
        <div class="flex flex-wrap items-center justify-between gap-4 bg-slate-950/90 p-4 rounded-xl border border-slate-800">
          <div class="flex items-center gap-2">
            <button
              @click="startSimulation"
              :disabled="isPlaying"
              class="px-4 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-500 disabled:opacity-50 text-white text-xs font-bold transition-all shadow-md shadow-indigo-600/20 flex items-center gap-1.5"
            >
              <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><polygon points="5 3 19 12 5 21 5 3"/></svg>
              자동 시뮬레이션
            </button>
            <button
              @click="nextStep"
              :disabled="isPlaying || currentStep >= totalSteps"
              class="px-4 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 disabled:opacity-50 text-slate-200 text-xs font-bold transition-all border border-slate-700 flex items-center gap-1.5"
            >
              다음 단계 진행 ➔
            </button>
            <button
              @click="resetSimulation"
              class="px-3 py-2 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-400 hover:text-white text-xs font-bold transition-all border border-slate-800"
            >
              🔄 초기화
            </button>
          </div>

          <!-- Step Progress Dots -->
          <div class="flex items-center gap-3">
            <span class="text-xs font-mono font-bold text-slate-400">Step {{ currentStep }} / {{ totalSteps }}</span>
            <div class="flex gap-1.5">
              <span
                v-for="s in totalSteps"
                :key="s"
                class="w-3 h-3 rounded-full transition-all duration-300"
                :class="s === currentStep ? 'scale-125 shadow-lg' : 'opacity-40'"
                :style="{ backgroundColor: s <= currentStep ? stitchSettings.colorHex : '#334155' }"
              ></span>
            </div>
          </div>
        </div>

        <!-- 4-Node Interactive Architecture Visual Canvas -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 relative z-10 items-stretch">

          <!-- Node 1: User -->
          <div
            @click="selectedComponent = 'user'"
            class="cursor-pointer bg-slate-950/90 p-5 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('user')"
          >
            <div>
              <div class="flex justify-between items-center mb-3">
                <span class="text-[11px] font-mono font-bold text-blue-400 uppercase tracking-wider">LAYER 1</span>
                <span class="px-2 py-0.5 rounded bg-blue-500/10 text-blue-300 text-[10px] font-mono font-bold">User</span>
              </div>

              <div class="flex items-center gap-3 mb-3">
                <div class="w-10 h-10 rounded-xl bg-blue-500/10 border border-blue-500/30 flex items-center justify-center text-blue-400 text-xl">
                  👤
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">사용자</h4>
                  <p class="text-xs text-slate-400">클릭 및 입력 동작</p>
                </div>
              </div>

              <div class="p-2.5 bg-slate-900/90 rounded-xl border border-slate-800 space-y-1.5 text-xs">
                <div class="flex justify-between">
                  <span class="text-amber-400 font-bold">HW:</span>
                  <span class="text-slate-300 font-mono">마우스/모니터/RAM</span>
                </div>
                <div class="flex justify-between border-t border-slate-800 pt-1">
                  <span class="text-emerald-400 font-bold">SW:</span>
                  <span class="text-slate-300 font-mono">OS / 브라우저 UI</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getUserStateText() }}</span>
              <span class="text-blue-400 font-bold text-xs">상세 🔍</span>
            </div>
          </div>

          <!-- Node 2: Frontend -->
          <div
            @click="selectedComponent = 'frontend'"
            class="cursor-pointer bg-slate-950/90 p-5 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('frontend')"
          >
            <div>
              <div class="flex justify-between items-center mb-3">
                <span class="text-[11px] font-mono font-bold text-cyan-400 uppercase tracking-wider">LAYER 2</span>
                <span class="px-2 py-0.5 rounded bg-cyan-500/10 text-cyan-300 text-[10px] font-mono font-bold">Frontend</span>
              </div>

              <div class="flex items-center gap-3 mb-3">
                <div class="w-10 h-10 rounded-xl bg-cyan-500/10 border border-cyan-500/30 flex items-center justify-center text-cyan-400 text-xl">
                  💻
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">프론트엔드</h4>
                  <p class="text-xs text-slate-400">Vue.js / 화면 렌더링</p>
                </div>
              </div>

              <div class="p-2.5 bg-slate-900/90 rounded-xl border border-slate-800 space-y-1.5 text-xs">
                <div class="flex justify-between">
                  <span class="text-amber-400 font-bold">HW:</span>
                  <span class="text-slate-300 font-mono">GPU / CDN 엣지</span>
                </div>
                <div class="flex justify-between border-t border-slate-800 pt-1">
                  <span class="text-emerald-400 font-bold">SW:</span>
                  <span class="text-slate-300 font-mono">Vue 3 / Fetch API</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getFrontendStateText() }}</span>
              <span class="text-cyan-400 font-bold text-xs">상세 🔍</span>
            </div>
          </div>

          <!-- Node 3: Backend -->
          <div
            @click="selectedComponent = 'backend'"
            class="cursor-pointer bg-slate-950/90 p-5 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('backend')"
          >
            <div>
              <div class="flex justify-between items-center mb-3">
                <span class="text-[11px] font-mono font-bold text-purple-400 uppercase tracking-wider">LAYER 3</span>
                <span class="px-2 py-0.5 rounded bg-purple-500/10 text-purple-300 text-[10px] font-mono font-bold">Backend</span>
              </div>

              <div class="flex items-center gap-3 mb-3">
                <div class="w-10 h-10 rounded-xl bg-purple-500/10 border border-purple-500/30 flex items-center justify-center text-purple-400 text-xl">
                  ⚙️
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">백엔드</h4>
                  <p class="text-xs text-slate-400">Node.js API 서버</p>
                </div>
              </div>

              <div class="p-2.5 bg-slate-900/90 rounded-xl border border-slate-800 space-y-1.5 text-xs">
                <div class="flex justify-between">
                  <span class="text-amber-400 font-bold">HW:</span>
                  <span class="text-slate-300 font-mono">서버 CPU / RAM</span>
                </div>
                <div class="flex justify-between border-t border-slate-800 pt-1">
                  <span class="text-emerald-400 font-bold">SW:</span>
                  <span class="text-slate-300 font-mono">Node.js / Express</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getBackendStateText() }}</span>
              <span class="text-purple-400 font-bold text-xs">상세 🔍</span>
            </div>
          </div>

          <!-- Node 4: Database -->
          <div
            @click="selectedComponent = 'database'"
            class="cursor-pointer bg-slate-950/90 p-5 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('database')"
          >
            <div>
              <div class="flex justify-between items-center mb-3">
                <span class="text-[11px] font-mono font-bold text-emerald-400 uppercase tracking-wider">LAYER 4</span>
                <span class="px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-300 text-[10px] font-mono font-bold">Database</span>
              </div>

              <div class="flex items-center gap-3 mb-3">
                <div class="w-10 h-10 rounded-xl bg-emerald-500/10 border border-emerald-500/30 flex items-center justify-center text-emerald-400 text-xl">
                  🗄️
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">데이터베이스</h4>
                  <p class="text-xs text-slate-400">PostgreSQL DBMS</p>
                </div>
              </div>

              <div class="p-2.5 bg-slate-900/90 rounded-xl border border-slate-800 space-y-1.5 text-xs">
                <div class="flex justify-between">
                  <span class="text-amber-400 font-bold">HW:</span>
                  <span class="text-slate-300 font-mono">NVMe SSD RAID</span>
                </div>
                <div class="flex justify-between border-t border-slate-800 pt-1">
                  <span class="text-emerald-400 font-bold">SW:</span>
                  <span class="text-slate-300 font-mono">PostgreSQL Engine</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getDatabaseStateText() }}</span>
              <span class="text-emerald-400 font-bold text-xs">상세 🔍</span>
            </div>
          </div>

        </div>

        <!-- Animated Stitched Dynamic Packet Flow Canvas -->
        <div class="py-4 border-t border-slate-800/80 space-y-2">
          <div class="flex justify-between w-full text-[11px] font-mono text-slate-400">
            <span>[User]</span>
            <span>[Frontend]</span>
            <span class="text-indigo-300 font-bold">Communication Stitch Thread ({{ currentScenario.method }})</span>
            <span>[Backend]</span>
            <span>[Database]</span>
          </div>

          <div class="relative w-full h-14 bg-slate-950 rounded-xl border border-slate-800 flex items-center px-4 overflow-hidden">
            <!-- Background Stitch Path Line -->
            <svg class="w-full h-full text-slate-800 overflow-visible" viewBox="0 0 1000 56" preserveAspectRatio="none">
              <path
                d="M 0,28 Q 250,8 500,28 T 1000,28"
                stroke="currentColor"
                :stroke-width="stitchSettings.thickness || 2"
                :stroke-dasharray="getConnectorDashArray()"
                fill="none"
              />
            </svg>

            <!-- Moving Packet Container -->
            <div
              class="absolute top-1/2 -translate-y-1/2 transition-all duration-500 ease-out flex items-center gap-2 px-3.5 py-1.5 rounded-lg border shadow-xl bg-slate-900/95 z-20"
              :style="packetPositionStyle"
            >
              <span class="w-2 h-2 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
              <span class="font-mono text-xs font-bold text-white whitespace-nowrap">
                {{ packetLabel }}
              </span>
            </div>
          </div>
        </div>

        <!-- Live Step Detail & Payload Inspector Panel -->
        <div class="p-6 rounded-2xl bg-slate-950 border border-slate-800 space-y-4">
          <div class="flex flex-wrap items-center justify-between gap-2 border-b border-slate-900 pb-3">
            <div class="flex items-center gap-2">
              <span class="px-2.5 py-0.5 rounded-full text-xs font-bold uppercase tracking-wider bg-indigo-500/10 text-indigo-300 border border-indigo-500/20">
                현재 단계 [Step {{ currentStep }} / {{ totalSteps }}]
              </span>
              <h4 class="text-base font-black text-white">{{ currentStepData.title }}</h4>
            </div>
            <span class="text-xs font-mono text-slate-400">방향: {{ currentStepData.direction }}</span>
          </div>

          <p class="text-base text-slate-300 leading-relaxed">
            {{ currentStepData.desc }}
          </p>

          <!-- Communication Message Payload Box -->
          <div class="p-3.5 bg-slate-900 rounded-xl border border-slate-800/90 font-mono text-xs space-y-1">
            <div class="flex justify-between text-slate-400 border-b border-slate-800 pb-1 text-[11px]">
              <span>전송 메시지 데이터 (Payload Inspector)</span>
              <span class="text-indigo-400 font-bold">{{ currentStepData.protocol }}</span>
            </div>
            <div class="text-emerald-400 pt-1 overflow-x-auto whitespace-pre-wrap font-mono leading-relaxed">
              {{ currentStepData.payload }}
            </div>
          </div>

          <!-- HW vs SW Involvement Matrix for this Step -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 pt-2">
            <div class="p-3 bg-slate-900/60 rounded-xl border border-slate-800">
              <span class="text-amber-400 font-bold text-xs flex items-center gap-1">
                <span>🔧</span> 하드웨어(HW) 동작:
              </span>
              <p class="text-base text-slate-300 mt-1 leading-relaxed">{{ currentStepData.hwAction }}</p>
            </div>
            <div class="p-3 bg-slate-900/60 rounded-xl border border-slate-800">
              <span class="text-emerald-400 font-bold text-xs flex items-center gap-1">
                <span>💻</span> 소프트웨어(SW) 동작:
              </span>
              <p class="text-base text-slate-300 mt-1 leading-relaxed">{{ currentStepData.swAction }}</p>
            </div>
          </div>
        </div>

      </div>
    </section>

    <!-- Deep Component Inspector Panel -->
    <section class="space-y-4" id="inspector-section">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h3 class="text-xl font-black text-white">4대 컴포넌트 심층 인스펙터 (Component Inspector)</h3>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        선택한 컴포넌트의 하드웨어 스펙, 소프트웨어 기술 스택, 통신 프로토콜 및 실무 Vibe Coding 팁을 자세히 학습합니다.
      </p>

      <div class="bg-slate-900/50 border border-slate-800 rounded-2xl p-6 space-y-6">
        <!-- Selector Tabs -->
        <div class="flex flex-wrap gap-2 border-b border-slate-800 pb-4">
          <button
            @click="selectedComponent = 'user'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'user' ? 'bg-blue-600 text-white border-blue-500 shadow-md shadow-blue-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            👤 01. 사용자 (User Tier)
          </button>
          <button
            @click="selectedComponent = 'frontend'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'frontend' ? 'bg-cyan-600 text-white border-cyan-500 shadow-md shadow-cyan-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            💻 02. 프론트엔드 (Frontend Tier)
          </button>
          <button
            @click="selectedComponent = 'backend'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'backend' ? 'bg-purple-600 text-white border-purple-500 shadow-md shadow-purple-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            ⚙️ 03. 백엔드 (Backend Tier)
          </button>
          <button
            @click="selectedComponent = 'database'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'database' ? 'bg-emerald-600 text-white border-emerald-500 shadow-md shadow-emerald-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            🗄️ 04. 데이터베이스 (Database Tier)
          </button>
        </div>

        <!-- Inspector Content Details -->
        <div class="space-y-6">
          <div class="flex items-center gap-3">
            <span class="text-3xl">{{ inspectorData.icon }}</span>
            <div>
              <h4 class="text-lg font-extrabold text-white">{{ inspectorData.title }}</h4>
              <p class="text-base text-slate-400">{{ inspectorData.subtitle }}</p>
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <!-- Hardware Spec Box -->
            <div class="bg-slate-950/80 p-5 rounded-xl border border-slate-800 space-y-3">
              <div class="flex items-center gap-2 text-amber-400 font-extrabold text-sm border-b border-slate-800/80 pb-2">
                <span>🔧 Hardware (하드웨어 역할 및 구조)</span>
              </div>
              <ul class="space-y-3 text-base text-slate-300">
                <li v-for="(item, idx) in inspectorData.hwList" :key="idx" class="flex items-start gap-2">
                  <span class="text-amber-400 font-bold">▪</span>
                  <div>
                    <strong class="text-white text-base">{{ item.name }}:</strong>
                    <p class="text-base text-slate-400 leading-relaxed mt-0.5">{{ item.desc }}</p>
                  </div>
                </li>
              </ul>
            </div>

            <!-- Software Spec Box -->
            <div class="bg-slate-950/80 p-5 rounded-xl border border-slate-800 space-y-3">
              <div class="flex items-center gap-2 text-emerald-400 font-extrabold text-sm border-b border-slate-800/80 pb-2">
                <span>💻 Software (소프트웨어 기술 스택)</span>
              </div>
              <ul class="space-y-3 text-base text-slate-300">
                <li v-for="(item, idx) in inspectorData.swList" :key="idx" class="flex items-start gap-2">
                  <span class="text-emerald-400 font-bold">▪</span>
                  <div>
                    <strong class="text-white text-base">{{ item.name }}:</strong>
                    <p class="text-base text-slate-400 leading-relaxed mt-0.5">{{ item.desc }}</p>
                  </div>
                </li>
              </ul>
            </div>
          </div>

          <!-- Protocol & Vibe Coding Tip Box -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div class="p-4 rounded-xl bg-indigo-950/30 border border-indigo-500/20 space-y-1">
              <h5 class="text-xs font-extrabold text-indigo-300 uppercase tracking-wider">📡 연관 통신 프로토콜</h5>
              <p class="text-base text-slate-200 leading-relaxed">{{ inspectorData.protocolInfo }}</p>
            </div>
            <div class="p-4 rounded-xl bg-purple-950/30 border border-purple-500/20 space-y-1">
              <h5 class="text-xs font-extrabold text-purple-300 uppercase tracking-wider">💡 Vibe Coding 실무 가이드</h5>
              <p class="text-base text-slate-200 leading-relaxed">{{ inspectorData.vibeTip }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'SystemSimulator',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const currentStep = ref(1)
    const totalSteps = 6
    const isPlaying = ref(false)
    const selectedScenarioKey = ref('search')
    const selectedComponent = ref('user')

    // Scenario datasets
    const scenarios = {
      search: {
        title: '[GET] 상품 및 데이터 검색',
        method: 'GET',
        endpoint: '/api/v1/products?q=vibe',
        steps: [
          {
            title: '01. 사용자 검색어 입력 및 클릭',
            direction: '사용자 ➔ 프론트엔드',
            protocol: 'DOM Event (input / click)',
            desc: '사용자가 웹 화면의 검색창에 "vibe"를 입력하고 [검색] 버튼을 클릭합니다.',
            payload: 'Event: click\nElement: &lt;button id="search-btn"&gt;검색&lt;/button&gt;\nValue: "vibe"',
            hwAction: '키보드/마우스 물리 입력 센서 동작 ➔ 메인 메모리(RAM) 인터럽트 발생',
            swAction: '브라우저 JS 이벤트 루프가 @click 핸들러 수신 ➔ 프론트엔드 입력 값 유효성 검사'
          },
          {
            title: '02. 프론트엔드 API 요청 생성 및 송출',
            direction: '프론트엔드 ➔ 백엔드',
            protocol: 'HTTP/1.1 GET Protocol',
            desc: '프론트엔드 앱이 REST API 규격에 맞는 GET 요청 패킷을 생성하여 백엔드 서버로 송신합니다.',
            payload: 'GET /api/v1/products?q=vibe HTTP/1.1\nHost: api.vibecoding.study\nAccept: application/json\nAuthorization: Bearer jwt_token_sample',
            hwAction: '클라이언트 랜카드(NIC) 전자기 신호 변환 ➔ 공유기 및 라우터 HW 송출',
            swAction: 'Fetch API / Axios 가 HTTP Request Header 생성 ➔ TCP/IP 암호화 패킷 전달'
          },
          {
            title: '03. 백엔드 요청 수신 및 SQL 쿼리 생성',
            direction: '백엔드 ➔ 데이터베이스',
            protocol: 'PostgreSQL Wire Protocol',
            desc: '백엔드 Node.js Express 서버가 요청을 받아 파라미터 파싱 후 DB 쿼리를 전송합니다.',
            payload: 'SELECT id, name, price, category FROM products WHERE name ILIKE \'%vibe%\' LIMIT 20;',
            hwAction: '백엔드 서버 NIC 신호 수신 ➔ CPU Multi-core 비즈니스 로직 연산',
            swAction: 'Express 라우터 통과 ➔ ORM/SQL Builder 가 인젝션 방지 처리된 SQL 질의문 생성'
          },
          {
            title: '04. 데이터베이스 쿼리 실행 및 레코드 추출',
            direction: '데이터베이스 ➔ 백엔드',
            protocol: 'DBMS Internal Memory Bus',
            desc: 'DB 엔진이 B-Tree 인덱스를 탐색하여 조건에 맞는 데이터를 NVMe SSD에서 조회 및 반환합니다.',
            payload: 'Result: 2 rows returned\nRows: [\n  { id: 101, name: "Vibe Note Pro", price: 29000 },\n  { id: 102, name: "Vibe Book", price: 15000 }\n]',
            hwAction: 'NVMe SSD 스토리지 RAID 컨트롤러 읽기 ➔ DB Server RAM 캐시 로딩',
            swAction: 'PostgreSQL DBMS Engine B-Tree Index Search ➔ Resultset 파싱'
          },
          {
            title: '05. 백엔드 JSON 응답 구성 및 송신',
            direction: '백엔드 ➔ 프론트엔드',
            protocol: 'HTTP/1.1 200 OK',
            desc: '백엔드 서버가 DB 조회 결과를 JSON 포맷으로 변환하고 HTTP 200 OK 상태 코드와 함께 반환합니다.',
            payload: 'HTTP/1.1 200 OK\nContent-Type: application/json\n\n{\n  "success": true,\n  "count": 2,\n  "data": [\n    { "id": 101, "name": "Vibe Note Pro", "price": 29000 },\n    { "id": 102, "name": "Vibe Book", "price": 15000 }\n  ]\n}',
            hwAction: '서버 NIC 패킷 발송 ➔ 통신사 백본 광케이블 및 5G/Wi-Fi 안테나 경유',
            swAction: 'Express res.json() 직렬화 ➔ Gzip 압축 및 CORS / Security Header 설정'
          },
          {
            title: '06. 프론트엔드 DOM 업데이트 및 화면 출력',
            direction: '프론트엔드 ➔ 사용자',
            protocol: 'Browser Render Pipeline',
            desc: '프론트엔드 반응형 상태(reactive state)가 업데이트되고, 브라우저가 화면을 최종 갱신합니다.',
            payload: 'Render: ProductsList.vue updated\nDOM Nodes: 2 List Cards Injected\nStatus: Render Complete (16ms)',
            hwAction: '클라이언트 GPU 프레임버퍼 픽셀 드로잉 ➔ OLED/LCD 모니터 화면 발광',
            swAction: 'Vue 3 Virtual DOM Diffing ➔ DOM Patch ➔ Blink Rendering Engine Layout/Paint'
          }
        ]
      },
      auth: {
        title: '[POST] 회원가입 및 로그인 처리',
        method: 'POST',
        endpoint: '/api/v1/auth/login',
        steps: [
          {
            title: '01. 사용자 로그인 정보 입력 및 Submit',
            direction: '사용자 ➔ 프론트엔드',
            protocol: 'DOM Submit Event',
            desc: '사용자가 이메일과 비밀번호를 입력하고 [로그인] 버튼을 누릅니다.',
            payload: 'Form: AuthForm.vue\nFields: { email: "user@vibe.com", password: "••••••••" }',
            hwAction: '터치스크린 압력 센서 또는 마우스 클릭 신호 발생 ➔ RAM 전달',
            swAction: '브라우저 폼 이벤트 가로채기(e.preventDefault) ➔ 이메일 정규식 유효성 검증'
          },
          {
            title: '02. 프론트엔드 암호화 요청 송신',
            direction: '프론트엔드 ➔ 백엔드',
            protocol: 'HTTPS TLS 1.3 POST Protocol',
            desc: '로그인 인증 요청을 HTTPS 암호화 터널을 통해 백엔드 인증 엔드포인트로 전송합니다.',
            payload: 'POST /api/v1/auth/login HTTP/1.1\nContent-Type: application/json\n\n{ "email": "user@vibe.com", "password": "mypassword123!" }',
            hwAction: '클라이언트 NIC 패킷 전송 ➔ SSL/TLS 암호화 모듈 통과',
            swAction: 'Axios POST 요청 ➔ TLS 1.3 클라이언트 핸드셰이크 암호화'
          },
          {
            title: '03. 백엔드 유저 조회 SQL 실행',
            direction: '백엔드 ➔ 데이터베이스',
            protocol: 'PostgreSQL Protocol',
            desc: '백엔드가 수신한 이메일 정보를 바탕으로 DB에서 해당 사용자 정보와 암호화 해시값을 조회합니다.',
            payload: 'SELECT id, email, password_hash, role FROM users WHERE email = \'user@vibe.com\';',
            hwAction: '서버 CPU 가 요청 해독 ➔ DB 서버 소켓 통신 전달',
            swAction: 'Express Auth Middleware ➔ DB 드라이버 질의 실행'
          },
          {
            title: '04. DB 사용자 해시 데이터 반환',
            direction: '데이터베이스 ➔ 백엔드',
            protocol: 'DBMS Internal Bus',
            desc: '데이터베이스가 이메일에 해당하는 사용자 레코드와 bcrypt 해시값을 반환합니다.',
            payload: 'Row Found: {\n  id: "usr_8823",\n  password_hash: "$2b$10$e8X...hashed_value",\n  role: "STUDENT"\n}',
            hwAction: 'DB SSD 스토리지 읽기 ➔ RAM 버퍼 로딩',
            swAction: 'PostgreSQL Index Lookup ➔ Recordset Return'
          },
          {
            title: '05. 백엔드 Bcrypt 검증 및 JWT 발급',
            direction: '백엔드 ➔ 프론트엔드',
            protocol: 'HTTP/1.1 200 OK + JWT',
            desc: '백엔드가 비밀번호 해시를 검증하고, 성공 시 서명된 JWT 토큰을 프론트엔드에 전달합니다.',
            payload: 'HTTP/1.1 200 OK\n\n{\n  "success": true,\n  "accessToken": "eyJhbGciOiJIUzI1NiR5...",\n  "user": { "id": "usr_8823", "name": "VibeUser" }\n}',
            hwAction: '백엔드 CPU 비밀번호 bcrypt 연산 처리 ➔ NIC 패킷 발송',
            swAction: 'bcrypt.compare() ➔ jsonwebtoken.sign() 발급 ➔ HTTP 응답'
          },
          {
            title: '06. 프론트엔드 토큰 저장 및 로그인 완료 화면 전환',
            direction: '프론트엔드 ➔ 사용자',
            protocol: 'LocalStorage / Pinia State',
            desc: '프론트엔드가 토큰을 안전하게 저장하고 인증된 메인 대시보드로 화면을 전환합니다.',
            payload: 'Storage: LocalStorage.setItem("access_token")\nRouter: router.push("/dashboard")\nView: DashboardView.vue rendered',
            hwAction: '스마트폰/PC GPU 대시보드 UI 렌더링 ➔ 화면 출력',
            swAction: 'Pinia userStore 인증 상태 true 변경 ➔ Vue Router Navigation Guard 통과'
          }
        ]
      },
      create: {
        title: '[POST] 게시글 작성 및 데이터 저장',
        method: 'POST',
        endpoint: '/api/v1/posts',
        steps: [
          {
            title: '01. 사용자 게시글 작성 및 저장 버튼 클릭',
            direction: '사용자 ➔ 프론트엔드',
            protocol: 'DOM Input Event',
            desc: '사용자가 제목과 본문을 입력하고 [저장하기] 버튼을 누릅니다.',
            payload: 'Form: CreatePost.vue\nTitle: "Vibe Coding 실습 후기"\nContent: "AI와 함께하는 개발이 매우 즐겁습니다."',
            hwAction: '키보드 입력 메인 메모리 전달 ➔ 디스플레이 모니터 파핑',
            swAction: 'v-model 데이터 바인딩 ➔ 필수 입력 항목 유효성 체크'
          },
          {
            title: '02. 프론트엔드 JSON 데이터 API 전송',
            direction: '프론트엔드 ➔ 백엔드',
            protocol: 'HTTP/1.1 POST Protocol',
            desc: '프론트엔드가 게시글 데이터를 JSON으로 패키징하여 API 서버로 전송합니다.',
            payload: 'POST /api/v1/posts HTTP/1.1\nContent-Type: application/json\nAuthorization: Bearer jwt_token\n\n{ "title": "Vibe Coding 실습 후기", "content": "..." }',
            hwAction: '클라이언트 NIC 데이터 전송 ➔ 인터넷 라우팅망 경유',
            swAction: 'Fetch API POST 전송 ➔ JWT 토큰 Auth Header 첨부'
          },
          {
            title: '03. 백엔드 트랜잭션 시작 및 DB INSERT 쿼리',
            direction: '백엔드 ➔ 데이터베이스',
            protocol: 'PostgreSQL Transaction',
            desc: '백엔드가 JWT 토큰의 권한을 확인하고, DB에 안전하게 저장하기 위한 INSERT 문을 실행합니다.',
            payload: 'BEGIN;\nINSERT INTO posts (title, content, author_id, created_at)\nVALUES (\'Vibe Coding 실습 후기\', \'...\', \'usr_8823\', NOW())\nRETURNING id;\nCOMMIT;',
            hwAction: '백엔드 CPU 토큰 검증 ➔ DB 서버 연결 수립',
            swAction: 'Auth Middleware JWT Verify ➔ ORM postRepository.save()'
          },
          {
            title: '04. DB 커밋 및 신규 생성 데이터 반환',
            direction: '데이터베이스 ➔ 백엔드',
            protocol: 'DBMS Commit Protocol',
            desc: '데이터베이스가 WAL(Write-Ahead Logging) 로그를 기록하고, 생성된 게시글 ID를 반환합니다.',
            payload: 'Transaction Committed Successfully\nInserted Record: { id: "post_9912", created_at: "2026-03-31T10:00:00Z" }',
            hwAction: 'NVMe SSD 스토리지 RAID 영구 저장 쓰기 ➔ RAM 기록',
            swAction: 'PostgreSQL ACID Transaction Commit ➔ RETURNING clause executed'
          },
          {
            title: '05. 백엔드 성공 응답 송신',
            direction: '백엔드 ➔ 프론트엔드',
            protocol: 'HTTP/1.1 201 Created',
            desc: '백엔드가 HTTP 201 Created 응답과 함께 생성된 게시글 객체를 반환합니다.',
            payload: 'HTTP/1.1 201 Created\n\n{\n  "success": true,\n  "message": "Post created successfully",\n  "post": { "id": "post_9912", "title": "Vibe Coding 실습 후기" }\n}',
            hwAction: '서버 NIC 패킷 송출 ➔ 네트워크 라우터 경유',
            swAction: 'Express res.status(201).json() 처리'
          },
          {
            title: '06. 프론트엔드 피드백 토스트 표시 및 피드 갱신',
            direction: '프론트엔드 ➔ 사용자',
            protocol: 'UI Reactive Render',
            desc: '프론트엔드가 "저장되었습니다" 토스트 알림을 띄우고 신규 글이 포함된 피드로 전환합니다.',
            payload: 'Toast: "게시글이 등록되었습니다! 🎉"\nFeed: FeedList.vue prepended with post_9912',
            hwAction: '클라이언트 GPU 화면 리드로잉 ➔ 사용자 모니터 출력',
            swAction: 'Vue 3 Reactive Array unshift() ➔ Toast Component Mount'
          }
        ]
      }
    }

    let intervalId = null

    const currentScenario = computed(() => scenarios[selectedScenarioKey.value])

    const onScenarioChange = () => {
      resetSimulation()
    }

    const startSimulation = () => {
      if (isPlaying.value) return
      isPlaying.value = true
      currentStep.value = 1

      intervalId = setInterval(() => {
        if (currentStep.value < totalSteps) {
          currentStep.value++
        } else {
          stopSimulation()
        }
      }, 2800)
    }

    const stopSimulation = () => {
      isPlaying.value = false
      if (intervalId) {
        clearInterval(intervalId)
        intervalId = null
      }
    }

    const nextStep = () => {
      if (currentStep.value < totalSteps) {
        currentStep.value++
      }
    }

    const resetSimulation = () => {
      stopSimulation()
      currentStep.value = 1
    }

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

    const isStepRelatedToComp = (compKey) => {
      if (compKey === 'user' && (currentStep.value === 1 || currentStep.value === 6)) return true
      if (compKey === 'frontend' && (currentStep.value === 1 || currentStep.value === 2 || currentStep.value === 5 || currentStep.value === 6)) return true
      if (compKey === 'backend' && (currentStep.value === 2 || currentStep.value === 3 || currentStep.value === 4 || currentStep.value === 5)) return true
      if (compKey === 'database' && (currentStep.value === 3 || currentStep.value === 4)) return true
      return false
    }

    const getComponentBorderStyle = (compKey) => {
      const isActive = isStepRelatedToComp(compKey) || selectedComponent.value === compKey
      const color = props.stitchSettings.colorHex || '#ec4899'
      const thick = isActive ? `${(props.stitchSettings.thickness || 2) + 1}px` : '1px'
      const style = isActive ? (props.stitchSettings.style || 'dashed') : 'solid'
      const borderColor = isActive ? color : '#1e293b'

      return {
        borderWidth: thick,
        borderColor: borderColor,
        borderStyle: style,
        boxShadow: isActive ? `0 4px 20px rgba(0,0,0,0.3), 0 0 15px ${color}25` : 'none'
      }
    }

    const getUserStateText = () => {
      if (currentStep.value === 1) return '입력 및 클릭 발생'
      if (currentStep.value === 6) return '최종 결과 화면 확인'
      return '대기 (Idle)'
    }

    const getFrontendStateText = () => {
      if (currentStep.value === 1) return '이벤트 수신 및 검증'
      if (currentStep.value === 2) return 'HTTP 요청 전송 중'
      if (currentStep.value === 5) return '응답 패킷 수신 중'
      if (currentStep.value === 6) return 'DOM 렌더링 중'
      return '대기 중'
    }

    const getBackendStateText = () => {
      if (currentStep.value === 2) return '요청 수신'
      if (currentStep.value === 3) return '비즈니스 로직 & DB 질의'
      if (currentStep.value === 4) return 'DB 결과 처리'
      if (currentStep.value === 5) return 'JSON 응답 발송'
      return '대기 중 (Listening)'
    }

    const getDatabaseStateText = () => {
      if (currentStep.value === 3) return 'SQL 쿼리 수신'
      if (currentStep.value === 4) return '인덱스 검색 & Commit'
      return '대기 중 (Ready)'
    }

    const getConnectorDashArray = () => {
      const style = props.stitchSettings.style
      const gap = props.stitchSettings.gap || 6
      const thick = props.stitchSettings.thickness || 2

      if (style === 'dotted') return `${thick} ${gap}`
      if (style === 'solid') return 'none'
      return `${gap * 1.5} ${gap}`
    }

    const packetPositionStyle = computed(() => {
      const color = props.stitchSettings.colorHex || '#ec4899'
      let leftPercent = '5%'

      if (currentStep.value === 1) leftPercent = '10%'
      else if (currentStep.value === 2) leftPercent = '28%'
      else if (currentStep.value === 3) leftPercent = '48%'
      else if (currentStep.value === 4) leftPercent = '68%'
      else if (currentStep.value === 5) leftPercent = '82%'
      else if (currentStep.value === 6) leftPercent = '92%'

      return {
        left: leftPercent,
        transform: 'translate(-50%, -50%)',
        borderColor: color,
        boxShadow: `0 0 12px ${color}40`
      }
    })

    const packetLabel = computed(() => {
      const scenario = currentScenario.value
      if (currentStep.value === 1) return `[User] Action Triggered`
      if (currentStep.value === 2) return `[Frontend ➔ Backend] ${scenario.method} ${scenario.endpoint}`
      if (currentStep.value === 3) return `[Backend ➔ Database] SQL Query Executing`
      if (currentStep.value === 4) return `[Database ➔ Backend] Recordset Returned`
      if (currentStep.value === 5) return `[Backend ➔ Frontend] HTTP 200/201 Success`
      return `[Frontend ➔ User] UI Render Complete`
    })

    const currentStepData = computed(() => {
      return currentScenario.value.steps[currentStep.value - 1]
    })

    // Component Inspector Detailed Info Data
    const inspectorData = computed(() => {
      if (selectedComponent.value === 'user') {
        return {
          icon: '👤',
          title: '01. 사용자 계층 (User Tier)',
          subtitle: '실제 단말기를 이용해 웹 서비스와 상호작용하는 엔드유저 영역',
          hwList: [
            { name: '사용자 단말 하드웨어', desc: '스마트폰(iPhone, Galaxy), 노크북, PC, 태블릿 등 기기 본체' },
            { name: '물리 입력 장치 (Input HW)', desc: '키보드, 마우스, 터치스크린 감압 센서, 마이크, 트랙패드' },
            { name: '디스플레이 장치 (Display HW)', desc: 'OLED/LCD 모니터 패널, 그래픽카드(GPU) 픽셀 버퍼' },
            { name: '단말 통신 모듈 (NIC HW)', desc: 'Wi-Fi 6 안테나, 5G/LTE 모뎀, 기가비트 이더넷 랜카드' }
          ],
          swList: [
            { name: '사용자 OS', desc: 'iOS, Android, Windows, macOS, Linux 등 물리 하드웨어를 제어하는 운영체제' },
            { name: '웹 브라우저 (Web Browser)', desc: 'Chrome, Safari, Edge 등 HTML/CSS/JS 웹 표준 구동 앱' },
            { name: '브라우저 이벤트 처리 엔진', desc: '사용자의 클릭, 키보드 입력, 스크롤 이벤트를 가로채는 OS/브라우저 수신기' }
          ],
          protocolInfo: 'DOM Event (click, input, submit), OS Hardware Interrupt',
          vibeTip: 'AI 기반 개발 시 사용자 모바일 기기 반응형 레이아웃과 터치 영역 UX를 프롬프트에 명시하세요.'
        }
      } else if (selectedComponent.value === 'frontend') {
        return {
          icon: '💻',
          title: '02. 프론트엔드 계층 (Frontend Tier)',
          subtitle: '사용자 브라우저에서 실행되는 클라이언트 애플리케이션',
          hwList: [
            { name: '클라이언트 CPU & GPU', desc: '브라우저 JS 컴파일(V8) 및 CSS/HTML 파싱, GPU 60fps 화면 렌더링 레지스터' },
            { name: 'CDN (Content Delivery Network) HW', desc: '전 세계 사용자와 가까운 엣지 서버(Edge Server) 랙 및 초고속 SSD' },
            { name: '메인 메모리 (System RAM)', desc: 'Vue/React 반응형 상태 객체 및 DOM 트리가 실시간 상주하는 RAM' }
          ],
          swList: [
            { name: '프론트엔드 프레임워크', desc: 'Vue 3, React, Next.js, Vite 빌드 도구' },
            { name: '웹 표준 언어 (Web Standards)', desc: 'HTML5 Semantic Tag, CSS Tailwind, Modern JavaScript (ES6+)' },
            { name: 'HTTP 통신 라이브러리', desc: 'Fetch API, Axios, TanStack Query (비동기 데이터 패칭 및 캐싱)' },
            { name: '상태 관리 및 라우팅', desc: 'Pinia, Redux, Vue Router (전역 앱 상태 및 페이지 전환)' }
          ],
          protocolInfo: 'HTTP/HTTPS, REST API, WebSockets, JSON Data Model',
          vibeTip: 'Stitch 디자인 시스템과 같이 재사용 가능한 UI 컴포넌트 구조를 설계하고 CSS 변수로 동적 테마를 적용하세요.'
        }
      } else if (selectedComponent.value === 'backend') {
        return {
          icon: '⚙️',
          title: '03. 백엔드 계층 (Backend Tier)',
          subtitle: '비즈니스 로직, 인증, 보안 및 데이터 처리를 담당하는 애플리케이션 서버',
          hwList: [
            { name: '클라우드 / 호스트 서버 (Server Chassis HW)', desc: '24시간 무중단 가동되는 서버 호스트, 데이터센터 랙 마운트' },
            { name: '서버 프로세서 (Multi-core CPU)', desc: '동시 다발적인 HTTP 요청을 수천 개 쓰레드로 병렬 처리하는 수십 코어 CPU' },
            { name: '서버 메모리 & 로드밸런서 HW', desc: '트래픽 분산을 위한 L4/L7 로드밸런서 및 서버 RAM' }
          ],
          swList: [
            { name: '서버 런타임 & 프레임워크', desc: 'Node.js (Express/NestJS), Java (Spring Boot), Python (FastAPI)' },
            { name: '웹 서버 데몬 (Reverse Proxy)', desc: 'Nginx, Apache, Caddy (SSL 종단 및 정적 라우팅)' },
            { name: '인증 & 미들웨어 (Security SW)', desc: 'JWT (JSON Web Token), OAuth 2.0, Bcrypt 비밀번호 해싱, CORS 설정' },
            { name: 'ORM & DB Connector', desc: 'Prisma, TypeORM, MyBatis, Sequelize (안전한 SQL 쿼리 생성)' }
          ],
          protocolInfo: 'HTTP/REST API, gRPC, TLS 1.3, DB Driver Protocol (TCP/IP)',
          vibeTip: '백엔드는 API 엔드포인트 명세(Spec)를 먼저 정의하고 에러 예외 처리 및 보안 검증을 철저히 설계하세요.'
        }
      } else {
        return {
          icon: '🗄️',
          title: '04. 데이터베이스 계층 (Database Tier)',
          subtitle: '서비스의 핵심 영구 데이터(Persistent Data)를 안전하게 저장하고 질의하는 DBMS',
          hwList: [
            { name: '고성능 NVMe SSD RAID 배열', desc: '초당 수만 번의 IOPS를 처리하는 데이터베이스 전용 고속 저장 장치' },
            { name: 'ECC RAM (Error-Correcting Memory)', desc: '메모리 비트 반전 오류를 자동 정정하여 DB 손상을 방지하는 메모리' },
            { name: '백업 전용 스토리제 & UPS', desc: '정전에 대비한 Uninterruptible Power Supply 및 자동 스냅샷 백업 HW' }
          ],
          swList: [
            { name: '관계형 / 비관계형 DBMS Engine', desc: 'PostgreSQL, MySQL, MongoDB, Redis (In-Memory Cache)' },
            { name: '쿼리 실행 및 인덱스 엔진', desc: 'B-Tree / Hash Indexer, Cost-based Query Optimizer' },
            { name: '트랜잭션 & ACID 복구 엔진', desc: 'WAL (Write-Ahead Logging), MVCC (Multi-Version Concurrency Control)' }
          ],
          protocolInfo: 'PostgreSQL Native Wire Protocol, MySQL Client/Server Protocol',
          vibeTip: '자주 조회되는 컬럼에 인덱스(Index)를 설정하고 데이터 무결성을 위한 외래키(FK) 조건을 올바르게 설정하세요.'
        }
      }
    })

    return {
      currentStep,
      totalSteps,
      isPlaying,
      selectedScenarioKey,
      selectedComponent,
      scenarios,
      currentScenario,
      onScenarioChange,
      startSimulation,
      stopSimulation,
      nextStep,
      resetSimulation,
      customStitchLineStyle,
      getComponentBorderStyle,
      getUserStateText,
      getFrontendStateText,
      getBackendStateText,
      getDatabaseStateText,
      getConnectorDashArray,
      packetPositionStyle,
      packetLabel,
      currentStepData,
      inspectorData
    }
  }
}
</script>
