<template>
  <div class="space-y-12">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 to-slate-900/90 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🖥️ INTERACTIVE WEB SYSTEM SIMULATOR
        </span>
        <h2 class="text-2xl sm:text-4xl font-black text-white tracking-tight mb-3">
          기본 웹 시스템 동작 시뮬레이션
        </h2>
        <p class="text-base text-slate-400 leading-relaxed max-w-3xl">
          사용자의 클릭 동작이 **브라우저**를 거쳐 **웹서버**로 전달되고, 다시 응답을 받아 화면에 표시되는 **웹 시스템의 기본 작동 과정**을 실시간 시뮬레이션합니다. 각 레이어별 **하드웨어(HW)**와 **소프트웨어(SW)**의 명확한 역할 구분을 체계적으로 학습해 보세요.
        </p>
      </div>

      <!-- Live Color Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Simulator</span>
      </div>
    </div>

    <!-- HW vs SW Classification Summary Matrix -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h3 class="text-xl font-black text-white">웹 시스템의 HW(하드웨어) vs SW(소프트웨어) 명확한 구분</h3>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        웹 시스템은 물체 형태를 가진 물리적 기기인 **하드웨어(HW)**와 그 위에서 실행되는 명령 집합인 **소프트웨어(SW)**가 유기적으로 맞물려 동작합니다.
      </p>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-2">
        <!-- 1. Client Layer -->
        <div class="bg-slate-900/60 p-6 rounded-2xl border border-slate-800 space-y-4">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-blue-400 uppercase tracking-wider">01. 사용자 & 클라이언트</span>
            <span class="px-2 py-0.5 rounded bg-blue-500/10 text-blue-300 border border-blue-500/20 text-[10px] font-bold">Client Tier</span>
          </div>
          <h4 class="text-base font-extrabold text-white">사용자 기기 영역</h4>

          <div class="space-y-3 text-base">
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>🔧 HW (하드웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                스마트폰, PC, 모니터, 키보드/마우스, 터치스크린, NIC(랜카드, Wi-Fi 안테나), RAM
              </p>
            </div>
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>💻 SW (소프트웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                운영체제(iOS/Android/Windows), 웹 브라우저(Chrome/Safari), 랜더링 엔진(Blink/WebKit), JS 엔진(V8)
              </p>
            </div>
          </div>
        </div>

        <!-- 2. Network Layer -->
        <div class="bg-slate-900/60 p-6 rounded-2xl border border-slate-800 space-y-4">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-purple-400 uppercase tracking-wider">02. 네트워크 매체</span>
            <span class="px-2 py-0.5 rounded bg-purple-500/10 text-purple-300 border border-purple-500/20 text-[10px] font-bold">Network Tier</span>
          </div>
          <h4 class="text-base font-extrabold text-white">통신 통로 영역</h4>

          <div class="space-y-3 text-base">
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>🔧 HW (하드웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                유무선 라우터(공유기), 광케이블, 기지국, L2/L3 스위치, 백본 관문 장비
              </p>
            </div>
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>💻 SW (소프트웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                TCP/IP 프로토콜 스택, DNS(도메인주소 변환), HTTP/HTTPS 통신 규격, TLS 암호화 프로토콜
              </p>
            </div>
          </div>
        </div>

        <!-- 3. Server Layer -->
        <div class="bg-slate-900/60 p-6 rounded-2xl border border-slate-800 space-y-4">
          <div class="flex items-center justify-between">
            <span class="text-xs font-mono font-bold text-emerald-400 uppercase tracking-wider">03. 웹 서버</span>
            <span class="px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-300 border border-emerald-500/20 text-[10px] font-bold">Server Tier</span>
          </div>
          <h4 class="text-base font-extrabold text-white">서버 호스트 영역</h4>

          <div class="space-y-3 text-base">
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-amber-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>🔧 HW (하드웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                고성능 데이터센터 랙 서버(CPU, ECC RAM, NVMe SSD 스토리제 레이드, Server NIC)
              </p>
            </div>
            <div class="p-3 bg-slate-950/80 rounded-xl border border-slate-800/80">
              <div class="flex items-center gap-1.5 text-emerald-400 font-bold text-xs uppercase tracking-wider mb-1">
                <span>💻 SW (소프트웨어)</span>
              </div>
              <p class="text-base text-slate-300 leading-relaxed">
                서버 OS(Linux/Ubuntu), 웹 서버 데몬(Nginx/Apache/Vite), 웹 애플리케이션(Node.js/Vue/API)
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Interactive Simulation Playground -->
    <section class="space-y-6">
      <div class="flex items-center justify-between border-b border-slate-900 pb-3">
        <div class="flex items-center gap-2">
          <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
          <h3 class="text-xl font-black text-white">실시간 라이브 웹 시스템 패킷 시뮬레이터</h3>
        </div>

        <!-- Simulation Controls -->
        <div class="flex items-center gap-2">
          <button
            @click="toggleRequestType"
            class="px-3 py-1.5 rounded-lg bg-slate-900 hover:bg-slate-800 border border-slate-700 text-xs font-bold text-indigo-300 transition-all flex items-center gap-1.5"
          >
            <span>요청 방식:</span>
            <span class="px-1.5 py-0.5 rounded bg-indigo-500/20 border border-indigo-500/40 text-white font-mono">{{ requestType }}</span>
          </button>
        </div>
      </div>

      <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 sm:p-8 relative overflow-hidden space-y-8">

        <!-- Top Control Bar -->
        <div class="flex flex-wrap items-center justify-between gap-4 bg-slate-950/80 p-4 rounded-xl border border-slate-800">
          <div class="flex items-center gap-2">
            <button
              @click="startSimulation"
              :disabled="isPlaying"
              class="px-4 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-500 disabled:opacity-50 text-white text-xs font-bold transition-all shadow-md flex items-center gap-1.5"
            >
              <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><polygon points="5 3 19 12 5 21 5 3"/></svg>
              자동 실행
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
          <div class="flex items-center gap-2">
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

        <!-- System Interactive Diagram Canvas -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 relative z-10 items-stretch">

          <!-- Block 1: User & Browser (Client Side) -->
          <div
            @click="selectedComponent = 'client'"
            class="cursor-pointer bg-slate-950/80 p-6 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('client')"
          >
            <div>
              <div class="flex justify-between items-center mb-4">
                <span class="text-[11px] font-mono font-bold text-blue-400 uppercase tracking-wider">CLIENT LAYER</span>
                <span class="px-2 py-0.5 rounded bg-blue-500/10 text-blue-300 text-[10px] font-mono">사용자 & 브라우저</span>
              </div>

              <!-- Node graphic -->
              <div class="flex items-center gap-3 mb-4">
                <div class="w-12 h-12 rounded-xl bg-blue-500/10 border border-blue-500/30 flex items-center justify-center text-blue-400 text-2xl">
                  👤
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">사용자 (User)</h4>
                  <p class="text-xs text-slate-400">마우스 클릭 / 키보드 입력</p>
                </div>
              </div>

              <div class="p-3 bg-slate-900/90 rounded-xl border border-slate-800 space-y-2">
                <div class="flex justify-between text-xs">
                  <span class="text-amber-400 font-bold">🔧 HW:</span>
                  <span class="text-slate-300 font-mono text-xs">입력장치, 모니터, RAM</span>
                </div>
                <div class="flex justify-between text-xs border-t border-slate-800 pt-1.5">
                  <span class="text-emerald-400 font-bold">💻 SW:</span>
                  <span class="text-slate-300 font-mono text-xs">웹 브라우저 (Chrome/Safari)</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getClientStateText() }}</span>
              <span class="text-blue-400 font-bold text-xs">클릭하여 명세 상세 보기 🔍</span>
            </div>
          </div>

          <!-- Block 2: Network Media & Protocols -->
          <div
            @click="selectedComponent = 'network'"
            class="cursor-pointer bg-slate-950/80 p-6 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('network')"
          >
            <div>
              <div class="flex justify-between items-center mb-4">
                <span class="text-[11px] font-mono font-bold text-purple-400 uppercase tracking-wider">NETWORK LAYER</span>
                <span class="px-2 py-0.5 rounded bg-purple-500/10 text-purple-300 text-[10px] font-mono">네트워크망</span>
              </div>

              <!-- Node graphic -->
              <div class="flex items-center gap-3 mb-4">
                <div class="w-12 h-12 rounded-xl bg-purple-500/10 border border-purple-500/30 flex items-center justify-center text-purple-400 text-2xl">
                  🌐
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">인터넷 통신망 (Network)</h4>
                  <p class="text-xs text-slate-400">DNS 조율 및 데이터 패킷 전송</p>
                </div>
              </div>

              <div class="p-3 bg-slate-900/90 rounded-xl border border-slate-800 space-y-2">
                <div class="flex justify-between text-xs">
                  <span class="text-amber-400 font-bold">🔧 HW:</span>
                  <span class="text-slate-300 font-mono text-xs">라우터, 스위치, 광케이블</span>
                </div>
                <div class="flex justify-between text-xs border-t border-slate-800 pt-1.5">
                  <span class="text-emerald-400 font-bold">💻 SW:</span>
                  <span class="text-slate-300 font-mono text-xs">TCP/IP, HTTP/HTTPS 규격</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getNetworkStateText() }}</span>
              <span class="text-purple-400 font-bold text-xs">클릭하여 명세 상세 보기 🔍</span>
            </div>
          </div>

          <!-- Block 3: Web Server Host -->
          <div
            @click="selectedComponent = 'server'"
            class="cursor-pointer bg-slate-950/80 p-6 rounded-2xl border transition-all duration-300 relative flex flex-col justify-between group"
            :style="getComponentBorderStyle('server')"
          >
            <div>
              <div class="flex justify-between items-center mb-4">
                <span class="text-[11px] font-mono font-bold text-emerald-400 uppercase tracking-wider">SERVER LAYER</span>
                <span class="px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-300 text-[10px] font-mono">웹 서버</span>
              </div>

              <!-- Node graphic -->
              <div class="flex items-center gap-3 mb-4">
                <div class="w-12 h-12 rounded-xl bg-emerald-500/10 border border-emerald-500/30 flex items-center justify-center text-emerald-400 text-2xl">
                  🗄️
                </div>
                <div>
                  <h4 class="text-base font-extrabold text-white">웹 서버 (Web Server)</h4>
                  <p class="text-xs text-slate-400">요청 수신, 정적 파일 및 API 처리</p>
                </div>
              </div>

              <div class="p-3 bg-slate-900/90 rounded-xl border border-slate-800 space-y-2">
                <div class="flex justify-between text-xs">
                  <span class="text-amber-400 font-bold">🔧 HW:</span>
                  <span class="text-slate-300 font-mono text-xs">서버 머신, CPU, SSD</span>
                </div>
                <div class="flex justify-between text-xs border-t border-slate-800 pt-1.5">
                  <span class="text-emerald-400 font-bold">💻 SW:</span>
                  <span class="text-slate-300 font-mono text-xs">Nginx/Vite, Node.js App</span>
                </div>
              </div>
            </div>

            <div class="mt-4 pt-3 border-t border-slate-800/80 text-[11px] text-slate-400 flex items-center justify-between">
              <span>상태: {{ getServerStateText() }}</span>
              <span class="text-emerald-400 font-bold text-xs">클릭하여 명세 상세 보기 🔍</span>
            </div>
          </div>

        </div>

        <!-- Dynamic Stitched Thread Packet Animation Lines -->
        <div class="py-4 border-t border-slate-800/80 flex flex-col items-center">
          <div class="flex justify-between w-full text-[10px] font-mono text-slate-400 mb-2">
            <span>[Client] Browser Event</span>
            <span class="text-indigo-400 font-bold">HTTP {{ requestType }} Protocol Packet Thread</span>
            <span>[Server] Web Response</span>
          </div>

          <div class="relative w-full h-12 bg-slate-950 rounded-xl border border-slate-800 flex items-center px-4 overflow-hidden">
            <!-- Background Stitch Line -->
            <svg class="w-full h-full text-slate-800 overflow-visible" viewBox="0 0 1000 48" preserveAspectRatio="none">
              <path
                d="M 0,24 Q 250,5 500,24 T 1000,24"
                stroke="currentColor"
                :stroke-width="stitchSettings.thickness || 2"
                :stroke-dasharray="getConnectorDashArray()"
                fill="none"
              />
            </svg>

            <!-- Animated Moving Packet Box -->
            <div
              class="absolute top-1/2 -translate-y-1/2 transition-all duration-500 ease-out flex items-center gap-2 px-3 py-1.5 rounded-lg border shadow-xl bg-slate-900 z-20"
              :style="packetPositionStyle"
            >
              <span class="w-2 h-2 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
              <span class="font-mono text-[11px] font-bold text-white whitespace-nowrap">
                {{ packetLabel }}
              </span>
            </div>
          </div>
        </div>

        <!-- Current Step Explanation Panel -->
        <div class="p-6 rounded-2xl bg-slate-950 border border-slate-800 space-y-3">
          <div class="flex items-center gap-2">
            <span class="px-2.5 py-0.5 rounded-full text-xs font-bold uppercase tracking-wider bg-indigo-500/10 text-indigo-300 border border-indigo-500/20">
              현재 시뮬레이션 단계 [Step {{ currentStep }}]
            </span>
            <h4 class="text-base font-black text-white">{{ currentStepTitle }}</h4>
          </div>

          <p class="text-base text-slate-300 leading-relaxed">
            {{ currentStepDescription }}
          </p>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-3 pt-3 border-t border-slate-900">
            <div class="p-3 bg-slate-900/60 rounded-xl border border-slate-800">
              <span class="text-amber-400 font-bold text-xs">🔧 이 단계의 HW(하드웨어) 개입:</span>
              <p class="text-base text-slate-400 mt-1 leading-relaxed">{{ currentStepHwAction }}</p>
            </div>
            <div class="p-3 bg-slate-900/60 rounded-xl border border-slate-800">
              <span class="text-emerald-400 font-bold text-xs">💻 이 단계의 SW(소프트웨어) 개입:</span>
              <p class="text-base text-slate-400 mt-1 leading-relaxed">{{ currentStepSwAction }}</p>
            </div>
          </div>
        </div>

      </div>
    </section>

    <!-- Detailed Interactive Component Inspector Panel -->
    <section class="space-y-4" id="inspector-section">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h3 class="text-xl font-black text-white">컴포넌트 상세 인스펙터 (Component Inspector)</h3>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        위 시뮬레이터 카드에서 관심 있는 영역을 선택하여 해당 컴포넌트 내부의 HW와 SW 구성 요소를 상세하게 분석합니다.
      </p>

      <div class="bg-slate-900/50 border border-slate-800 rounded-2xl p-6 space-y-6">
        <!-- Component selector tabs -->
        <div class="flex flex-wrap gap-2 border-b border-slate-800 pb-4">
          <button
            @click="selectedComponent = 'client'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'client' ? 'bg-blue-600 text-white border-blue-500 shadow-md shadow-blue-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            👤 사용자 & 클라이언트 (Client)
          </button>
          <button
            @click="selectedComponent = 'network'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'network' ? 'bg-purple-600 text-white border-purple-500 shadow-md shadow-purple-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            🌐 네트워크 & 통신 규격 (Network)
          </button>
          <button
            @click="selectedComponent = 'server'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all border"
            :class="selectedComponent === 'server' ? 'bg-emerald-600 text-white border-emerald-500 shadow-md shadow-emerald-600/20' : 'bg-slate-950 text-slate-400 border-slate-800 hover:text-white'"
          >
            🗄️ 웹 서버 & 백엔드 (Server)
          </button>
        </div>

        <!-- Inspector Content -->
        <div class="space-y-6">
          <div class="flex items-center gap-3">
            <span class="text-2xl">{{ inspectorData.icon }}</span>
            <div>
              <h4 class="text-lg font-extrabold text-white">{{ inspectorData.title }}</h4>
              <p class="text-base text-slate-400">{{ inspectorData.subtitle }}</p>
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <!-- Hardware Spec Card -->
            <div class="bg-slate-950/80 p-5 rounded-xl border border-slate-800 space-y-3">
              <div class="flex items-center gap-2 text-amber-400 font-extrabold text-sm border-b border-slate-800/80 pb-2">
                <span>🔧 Hardware (하드웨어 사양)</span>
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

            <!-- Software Spec Card -->
            <div class="bg-slate-950/80 p-5 rounded-xl border border-slate-800 space-y-3">
              <div class="flex items-center gap-2 text-emerald-400 font-extrabold text-sm border-b border-slate-800/80 pb-2">
                <span>💻 Software (소프트웨어 사양)</span>
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

          <!-- Educational Summary Box -->
          <div class="p-4 rounded-xl bg-indigo-950/20 border border-indigo-500/20">
            <h5 class="text-sm font-extrabold text-indigo-300 mb-1">💡 핵심 요약</h5>
            <p class="text-base text-slate-300 leading-relaxed">
              {{ inspectorData.summary }}
            </p>
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
    const totalSteps = 5
    const isPlaying = ref(false)
    const requestType = ref('GET')
    const selectedComponent = ref('client')

    const toggleRequestType = () => {
      requestType.value = requestType.value === 'GET' ? 'POST' : 'GET'
    }

    let intervalId = null

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
      }, 2500)
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

    const isStepRelatedToComp = (compKey) => {
      if (compKey === 'client' && (currentStep.value === 1 || currentStep.value === 5)) return true
      if (compKey === 'network' && (currentStep.value === 2 || currentStep.value === 4)) return true
      if (compKey === 'server' && currentStep.value === 3) return true
      return false
    }

    const getClientStateText = () => {
      if (currentStep.value === 1) return '입력 이벤트 감지 중'
      if (currentStep.value === 5) return '화면 수신 및 랜더링 중'
      return '대기 중 (Idle)'
    }

    const getNetworkStateText = () => {
      if (currentStep.value === 2) return `HTTP ${requestType.value} 패킷 서버 전송 중`
      if (currentStep.value === 4) return 'HTTP 200 OK 응답 패킷 클라이언트 전송 중'
      return '통신 준비 완료'
    }

    const getServerStateText = () => {
      if (currentStep.value === 3) return '요청 수신 및 비즈니스 로직 실행 중'
      return '서버 대기 중 (Listening on Port 80/443)'
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

      if (currentStep.value === 1) leftPercent = '8%'
      else if (currentStep.value === 2) leftPercent = '32%'
      else if (currentStep.value === 3) leftPercent = '50%'
      else if (currentStep.value === 4) leftPercent = '72%'
      else if (currentStep.value === 5) leftPercent = '92%'

      return {
        left: leftPercent,
        transform: 'translate(-50%, -50%)',
        borderColor: color,
        boxShadow: `0 0 12px ${color}40`
      }
    })

    const packetLabel = computed(() => {
      if (currentStep.value === 1) return `[Client] ${requestType.value} Event Triggered`
      if (currentStep.value === 2) return `[Request] ${requestType.value} /index.html`
      if (currentStep.value === 3) return `[Server] Processing Request...`
      if (currentStep.value === 4) return `[Response] HTTP/1.1 200 OK`
      return `[Client] DOM Rendered`
    })

    // Step Explanations
    const currentStepTitle = computed(() => {
      if (currentStep.value === 1) return '사용자 이벤트 발생 및 브라우저 이벤트 캡처'
      if (currentStep.value === 2) return 'DNS 조회 및 네트워크 패킷 전송 (Client ➔ Server)'
      if (currentStep.value === 3) return '웹 서버 수신, 파일 조회 / API 로직 처리'
      if (currentStep.value === 4) return '응답 데이터 패킷 전송 (Server ➔ Client)'
      return '브라우저 랜더링 엔진 작동 및 화면 출력 완료'
    })

    const currentStepDescription = computed(() => {
      if (currentStep.value === 1) {
        return `사용자가 모니터 화면을 보며 마우스를 클릭하거나 URL을 입력합니다. 입력 신호는 키보드/마우스 HW 센서를 타고 OS를 거쳐 웹 브라우저(SW) 이벤트 루프에 전달됩니다.`
      }
      if (currentStep.value === 2) {
        return `브라우저는 도메인을 IP 주소로 변환(DNS)하고 HTTP ${requestType.value} 요청 헤더와 바디를 구성합니다. 이 데이터는 랜카드(NIC)를 통해 전자기/광신호로 변환되어 라우터와 네트워크 광케이블(HW)을 통해 서버로 이동합니다.`
      }
      if (currentStep.value === 3) {
        return `웹 서버 머신의 NIC와 CPU가 전자기 신호를 가로채 Linux OS 소켓에 넘깁니다. Nginx / Node.js 웹 서버(SW)가 요청 주소를 분석하고 HTML, CSS, JS 파일을 디스크에서 읽거나 DB 조회를 실행합니다.`
      }
      if (currentStep.value === 4) {
        return `웹 서버는 처리된 결과(HTML/JSON)를 HTTP 200 OK 응답 상태 코드와 함께 패킷으로 포장합니다. 서버 NIC HW에서 전기 신호로 다시 복출되어 네트워크망을 지나 클라이언트 랜카드로 돌아옵니다.`
      }
      return `클라이언트 브라우저의 DOM 파서, CSSOM 파서 및 V8 JS 엔진(SW)이 전달받은 응답 코드를 해석합니다. GPU/그래픽 카드(HW)가 피셀 단위로 픽셀을 드로잉하여 최종 결과를 모니터에 표시합니다.`
    })

    const currentStepHwAction = computed(() => {
      if (currentStep.value === 1) return '마우스/터치 센서 압력 감지 ➔ 클라이언트 컴퓨터 RAM 메인 메모리에 신호 전달'
      if (currentStep.value === 2) return '클라이언트 랜카드(NIC) 패킷 발송 ➔ 유무선 공유기/광케이블 라우팅'
      if (currentStep.value === 3) return '서버 NIC 랜카드 신호 수신 ➔ 서버 메인board CPU 데이터 처리 및 SSD 읽기'
      if (currentStep.value === 4) return '서버 데이터센터 라우터 패킷 송출 ➔ 해저 광케이블 및 기지국 경유'
      return '클라이언트 그래픽카드(GPU) 프레임 버퍼 생성 ➔ 모니터 디스플레이 패널 빛 발광'
    })

    const currentStepSwAction = computed(() => {
      if (currentStep.value === 1) return 'Windows/macOS OS 이벤트 핸들러 ➔ 브라우저(Chrome) click/submit 이벤트 감지'
      if (currentStep.value === 2) return 'TCP/IP 3-Way Handshake 맺기 ➔ HTTP GET/POST 헤더 생성 ➔ TLS 암호화'
      if (currentStep.value === 3) return 'Nginx/Node.js 라우팅 핸들러 수신 ➔ 정적 파일 전달 또는 Vue/API 스크립트 실행'
      if (currentStep.value === 4) return 'HTTP 200 OK 응답 헤더 구성 ➔ Content-Type: text/html 헤더 세팅'
      return 'Blink 랜더링 엔진 HTML Parsing ➔ CSSOM 트리기반 Layout/Paint ➔ JS Event Loop 재가동'
    })

    // Component Inspector Data
    const inspectorData = computed(() => {
      if (selectedComponent.value === 'client') {
        return {
          icon: '👤',
          title: '클라이언트 및 사용자 단 (Client Tier)',
          subtitle: '사용자가 직접 인터랙션하고 결과를 보는 프론트엔드 환경',
          hwList: [
            { name: '입력 장치 (Input Hardware)', desc: '키보드, 마우스, 모바일 가속도계 및 터치스크린 등 물리 신호 수집 장치' },
            { name: '디스플레이 장치 (Display Hardware)', desc: 'OLED/LCD 모니터 패널, GPU(그래픽 처리 장치) 프레임 버퍼' },
            { name: '통신 모듈 (Network Hardware)', desc: 'Wi-Fi 6 안테나, 5G/LTE 모뎀, 기가비트 이더넷 랜카드(NIC)' },
            { name: '주기억장치 (Memory Hardware)', desc: '브라우저 탭 및 DOM 트리가 상주하는 메모리(System RAM)' }
          ],
          swList: [
            { name: '클라이언트 OS', desc: 'Windows, macOS, iOS, Android 등 하드웨어 자원을 추상화하는 시스템 소프트웨어' },
            { name: '웹 브라우저 (Web Browser)', desc: 'Chrome, Safari, Edge 등 웹 표준을 준수하는 응용 프로그램' },
            { name: '브라우저 엔진 (Rendering & JS Engine)', desc: 'HTML/CSS를 화면으로 바꾸는 Blink/WebKit 및 자바스크립트를 컴파일하는 V8 엔진' },
            { name: '프론트엔드 코드 (Client Code)', desc: 'Vue.js, React 등으로 빌드된 HTML structure, CSS stylesheet, JS logic' }
          ],
          summary: '클라이언트 측에서는 사용자의 물리적 행동(HW)이 브라우저 엔진(SW)에 의해 네트워크 메시지로 변환되는 거점입니다.'
        }
      } else if (selectedComponent.value === 'network') {
        return {
          icon: '🌐',
          title: '네트워크 통신 매체 단 (Network Tier)',
          subtitle: '클라이언트와 서버 간 데이터 패킷을 중계하는 전달망',
          hwList: [
            { name: '게이트웨이 & 공유기 (Router HW)', desc: '패킷의 최적 경로를 지정하고 IP 주소를 변환(NAT)하는 통신 장비' },
            { name: '전송 매체 (Physical Cable HW)', desc: '빛의 전반사를 이용해 데이터를 빛으로 보낸 해저 광케이블 및 UTP 선' },
            { name: '스위칭 장비 (L2/L3 Switch HW)', desc: '데이터 센터 및 ISP 내부에서 MAC 주소를 기반으로 패킷을 고속 스위칭' }
          ],
          swList: [
            { name: 'DNS (Domain Name System SW)', desc: 'google.com 과 같은 문자를 142.250.x.x 와 같은 IP 주소로 변환하는 소프트웨어' },
            { name: 'TCP/IP 프로토콜 스택', desc: '패킷 분할, 순서 보장, 신뢰성 제어(TCP) 및 패킷 주소 지정(IP) 통신 규약' },
            { name: 'HTTP / HTTPS 규격 (Application SW)', desc: '웹 데이터를 주고받는 표준 애플리케이션 계층 약속 (Header, Body, Status Code)' },
            { name: 'TLS / SSL 암호화 소프트웨어', desc: '네트워크 중간 도청을 방지하기 위해 패킷 데이터를 복호화 불가능하게 암호화' }
          ],
          summary: '네트워크 통신망은 물리 케이블(HW) 위에 TCP/IP 및 HTTP 규칙(SW)이 얹혀 정확한 대상에게 전송되도록 보장합니다.'
        }
      } else {
        return {
          icon: '🗄️',
          title: '웹 서버 및 백엔드 단 (Server Tier)',
          subtitle: '비즈니스 로직을 처리하고 고성능 호스팅을 제공하는 서버',
          hwList: [
            { name: '랙형 서버 머신 (Server Chassis HW)', desc: '24시간 365일 무중단 가동되는 데이터센터 랙 마운트 전용 컴퓨터' },
            { name: '서버 CPU & ECC 메모리', desc: '다중 요청을 동시 처리하는 수십 코어 프로세서 및 데이터 오류를 자동 정정하는 RAM' },
            { name: 'NVMe SSD 스토리지 (RAID HW)', desc: '웹 정적 파일 및 데이터베이스를 초고속으로 읽고 쓰기 위한 디스크 배열' },
            { name: '고성능 서버 NIC (Server Network Card)', desc: '10Gbps ~ 100Gbps 대역폭을 지원하는 서버 전용 멀티포트 랜카드' }
          ],
          swList: [
            { name: '서버 OS (Server Operating System)', desc: 'Ubuntu Linux, RedHat, Debian 등 안정성이 검증된 POSIX 기반 운영체제' },
            { name: '웹 서버 데몬 (Web Server SW)', desc: 'Nginx, Apache, Vite Dev Server 등 80/443 포트로 들어오는 HTTP 요청을 최초 수신하는 서버' },
            { name: '웹 애플리케이션 / API 스크립트', desc: 'Node.js, Express, Python FastAPI, Vue SSR 등 요청을 받아 DB 처리 및 JSON/HTML 생성' },
            { name: '데이터베이스 (Database Management SW)', desc: 'MySQL, PostgreSQL, MongoDB 등 비즈니스 데이터를 영구 보관하고 질의 처리하는 SW' }
          ],
          summary: '서버 측은 고성능 서버 머신(HW)에서 웹 서버 소프트웨어(SW)가 대기하며 들어오는 요청을 1초 안에 처리하여 응답을 송출합니다.'
        }
      }
    })

    return {
      currentStep,
      totalSteps,
      isPlaying,
      requestType,
      selectedComponent,
      toggleRequestType,
      startSimulation,
      stopSimulation,
      nextStep,
      resetSimulation,
      customStitchLineStyle,
      getComponentBorderStyle,
      getClientStateText,
      getNetworkStateText,
      getServerStateText,
      getConnectorDashArray,
      packetPositionStyle,
      packetLabel,
      currentStepTitle,
      currentStepDescription,
      currentStepHwAction,
      currentStepSwAction,
      inspectorData
    }
  }
}
</script>
