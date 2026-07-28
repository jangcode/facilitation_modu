<template>
  <div class="space-y-12">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 to-slate-900/90 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🌐 SYSTEM ENVIRONMENTS & TECH STACK
        </span>
        <h2 class="text-2xl sm:text-3xl font-black text-white tracking-tight mb-3">
          시스템 실행, 개발, 운영 환경 및 기술 스택
        </h2>
        <p class="text-base text-slate-400 leading-relaxed max-w-3xl">
          Vibe Coding Study Note가 실행되고, 개발되며, 운영(배포)되는 전체 환경을 한눈에 파악합니다. 각 환경의 역할과 상세 기술 스택을 분석하고, **Stitch MCP(Multi-environment Control Panel)**를 통해 실시간 데이터와 코드의 흐름을 확인해 보세요.
        </p>
      </div>

      <!-- Live Color Dot Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Link</span>
      </div>
    </div>

    <!-- Interactive Stitch MCP (Multi-environment Control Playground) Infographic -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">Stitch MCP (Multi-environment Connector & Control Playground)</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        아래의 인터랙티브 인포그래픽을 통해 각 환경 간 코드 전달 흐름과 기술 연결성을 제어해 보세요. 각 환경 노드를 클릭하면 해당 환경의 상세 핵심 요약과 맞춤 제안이 하단 정보창에 활성화됩니다.
      </p>

      <div class="bg-slate-900/60 border border-slate-800 rounded-2xl p-6 sm:p-8 relative overflow-hidden">
        <!-- Stitch MCP Grid & SVG Connectors -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 relative z-10 items-stretch">

          <!-- Node 1: Development Environment -->
          <div
            @click="activeNode = 'dev'"
            class="cursor-pointer bg-slate-950/60 p-6 rounded-xl border transition-all duration-300 relative flex flex-col justify-between hover:bg-slate-950/90"
            :style="getNodeBorderStyle('dev')"
          >
            <div>
              <div class="flex justify-between items-start mb-4">
                <span class="text-[10px] font-mono text-blue-400 font-bold uppercase tracking-wider">💻 Environment 01</span>
                <span class="w-2.5 h-2.5 rounded-full" :class="activeNode === 'dev' ? 'bg-blue-400 animate-pulse' : 'bg-slate-800'"></span>
              </div>
              <div class="w-10 h-10 rounded-lg bg-blue-500/10 text-blue-400 flex items-center justify-center border border-blue-500/20 mb-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                  <line x1="8" y1="21" x2="16" y2="21"/>
                  <line x1="12" y1="17" x2="12" y2="21"/>
                </svg>
              </div>
              <h5 class="text-base font-extrabold text-white mb-2">개발 환경 (Development)</h5>
              <p class="text-xs text-slate-400 leading-relaxed">
                사용자의 아이디어 발제와 이슈 관리가 일어나는 시발점입니다. 모바일 기기의 GitHub 앱이나 로컬 워크스페이스를 통해 요구사항이 등록됩니다.
              </p>
            </div>
            <div class="mt-4 pt-3 border-t border-slate-800/60 flex flex-wrap gap-1.5">
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Vue 3</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Git/GitHub</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Tailwind</span>
            </div>
          </div>

          <!-- Node 2: Runtime Environment (Sandbox) -->
          <div
            @click="activeNode = 'runtime'"
            class="cursor-pointer bg-slate-950/60 p-6 rounded-xl border transition-all duration-300 relative flex flex-col justify-between hover:bg-slate-950/90"
            :style="getNodeBorderStyle('runtime')"
          >
            <div>
              <div class="flex justify-between items-start mb-4">
                <span class="text-[10px] font-mono text-purple-400 font-bold uppercase tracking-wider">⚙️ Environment 02</span>
                <span class="w-2.5 h-2.5 rounded-full" :class="activeNode === 'runtime' ? 'bg-purple-400 animate-pulse' : 'bg-slate-800'"></span>
              </div>
              <div class="w-10 h-10 rounded-lg bg-purple-500/10 text-purple-400 flex items-center justify-center border border-purple-500/20 mb-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/>
                </svg>
              </div>
              <h5 class="text-base font-extrabold text-white mb-2">실행 환경 (Runtime)</h5>
              <p class="text-xs text-slate-400 leading-relaxed">
                AI 에이전트 Jules가 직접 패키지를 설치하고, 코드를 작성하며, 빌드 테스트를 자동 수행하는 가상 샌드박스 안전 격리 컨테이너 환경입니다.
              </p>
            </div>
            <div class="mt-4 pt-3 border-t border-slate-800/60 flex flex-wrap gap-1.5">
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Node.js</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Bun/npm</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Bash Shell</span>
            </div>
          </div>

          <!-- Node 3: Production Environment -->
          <div
            @click="activeNode = 'prod'"
            class="cursor-pointer bg-slate-950/60 p-6 rounded-xl border transition-all duration-300 relative flex flex-col justify-between hover:bg-slate-950/90"
            :style="getNodeBorderStyle('prod')"
          >
            <div>
              <div class="flex justify-between items-start mb-4">
                <span class="text-[10px] font-mono text-emerald-400 font-bold uppercase tracking-wider">🚀 Environment 03</span>
                <span class="w-2.5 h-2.5 rounded-full" :class="activeNode === 'prod' ? 'bg-emerald-400 animate-pulse' : 'bg-slate-800'"></span>
              </div>
              <div class="w-10 h-10 rounded-lg bg-emerald-500/10 text-emerald-400 flex items-center justify-center border border-emerald-500/20 mb-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/>
                </svg>
              </div>
              <h5 class="text-base font-extrabold text-white mb-2">운영 환경 (Production)</h5>
              <p class="text-xs text-slate-400 leading-relaxed">
                Jules가 제출한 PR이 머지되면 Vercel 클라우드의 고성능 글로벌 엣지 네트워크에 서버리스 아키텍처로 자동 빌드 및 배포되는 환경입니다.
              </p>
            </div>
            <div class="mt-4 pt-3 border-t border-slate-800/60 flex flex-wrap gap-1.5">
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Vercel</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">Edge CDN</span>
              <span class="px-2 py-0.5 rounded bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-mono">SSL/DNS</span>
            </div>
          </div>

        </div>

        <!-- Stitched Thread Flow Lines (Visualizing the Connection via SVG) -->
        <div class="mt-8 pt-6 border-t border-slate-800/50 flex flex-col items-center">
          <div class="text-[10px] font-mono text-slate-500 uppercase tracking-wider mb-2">Stitch MCP Live Connectivity Map</div>
          <svg class="w-full h-12 text-slate-800 overflow-visible" viewBox="0 0 600 24" fill="none">
            <path
              :d="getMcpPath()"
              stroke="currentColor"
              :stroke-width="stitchSettings.thickness || 2"
              :stroke-dasharray="getMcpDashArray()"
              :style="getMcpAnimationStyle()"
              stroke-linecap="round"
            />
            <circle cx="50" cy="12" r="4" :fill="stitchSettings.colorHex" />
            <circle cx="300" cy="12" r="4" :fill="stitchSettings.colorHex" />
            <circle cx="550" cy="12" r="4" :fill="stitchSettings.colorHex" />
          </svg>
          <div class="w-full flex justify-between text-[9px] font-mono text-slate-500 px-2 sm:px-12 mt-1">
            <span>Issue Assigned (개발 -> 실행)</span>
            <span>PR Submitted & Build Test (실행 -> 운영)</span>
          </div>
        </div>

        <!-- Interactive Playground Display -->
        <div class="mt-8 p-5 rounded-xl bg-slate-950 border border-slate-800/80">
          <div class="flex items-center gap-2 mb-3">
            <span class="inline-block w-2 h-2 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
            <span class="text-xs font-mono text-slate-400 uppercase tracking-wider">MCP Dynamic Details: {{ activeNodeName }}</span>
          </div>
          <p class="text-base text-slate-300 leading-relaxed">
            {{ activeNodeDescription }}
          </p>
        </div>

      </div>
    </section>

    <!-- Deep Tech Stack Breakdown & Core Details -->
    <section class="space-y-8">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">상세 환경별 기술 스택 사양서</h4>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">

        <!-- Tech Card 1 -->
        <div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6 flex flex-col justify-between">
          <div>
            <div class="flex items-center gap-2.5 mb-4">
              <div class="w-8 h-8 rounded-lg bg-blue-500/10 text-blue-400 flex items-center justify-center border border-blue-500/20">
                <span class="font-bold text-xs">DEV</span>
              </div>
              <h5 class="text-base font-extrabold text-white">개발 환경 기술 명세</h5>
            </div>
            <p class="text-base text-slate-400 leading-relaxed mb-6">
              Vibe Coding의 핵심은 가볍고 즉각적인 기획 전환입니다. 로컬 PC에 번거로운 SDK를 모두 설치하지 않아도, GitHub 브라우저 환경 및 모바일 클라이언트에서 바로 이슈를 등록하고 제어할 수 있는 유연한 워크플로우를 보장합니다.
            </p>
            <ul class="space-y-3.5 text-xs text-slate-300">
              <li class="flex items-start gap-2">
                <span class="text-blue-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">GitHub Client Framework:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">모바일 GitHub 공식 App을 활용한 신속한 UI 개선 및 에이전트 할당 시스템.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-blue-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Vue 3 Single Page App:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">Composition API와 정적 상태 관리를 활용한 고성능 사용자 반응형 대시보드.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-blue-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Tailwind CSS v3:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">디자인 시스템 규격을 클래스 단위로 모듈화하여 일관성 있는 스타일링 지원.</p>
                </div>
              </li>
            </ul>
          </div>
          <div class="mt-6 pt-4 border-t border-slate-800/50 flex justify-between items-center text-[10px] font-mono text-slate-500">
            <span>Primary Focus</span>
            <span class="text-blue-400 font-bold">Productivity & Mobility</span>
          </div>
        </div>

        <!-- Tech Card 2 -->
        <div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6 flex flex-col justify-between">
          <div>
            <div class="flex items-center gap-2.5 mb-4">
              <div class="w-8 h-8 rounded-lg bg-purple-500/10 text-purple-400 flex items-center justify-center border border-purple-500/20">
                <span class="font-bold text-xs">RUN</span>
              </div>
              <h5 class="text-base font-extrabold text-white">실행 환경 기술 명세</h5>
            </div>
            <p class="text-base text-slate-400 leading-relaxed mb-6">
              AI 에이전트 Jules가 코드를 빌드하고 시뮬레이션을 수행하는 가상 실행 엔진입니다. 외부 망과의 통신 제어 및 패키지 관리, 가상 셸 스크립트 실행 환경을 완벽히 격리하여 안전하고 정확한 산출물을 검증합니다.
            </p>
            <ul class="space-y-3.5 text-xs text-slate-300">
              <li class="flex items-start gap-2">
                <span class="text-purple-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Isolated Sandbox Sandbox:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">메모리 격리 기반 가상 머신으로, 에이전트 오염 물질의 차단 및 가상 셸 명령어 실행 지원.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-purple-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Node.js Runtime & NPM:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">안정적인 패키지 생태계와 빌드 의존성 관리를 위한 최신 롱텀 서포트 런타임 탑재.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-purple-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Vite Build Tool:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">초고속 번들러 및 빌드 캐싱으로, Jules의 빌드 검증 속도를 극대화하여 피드백 주기 최소화.</p>
                </div>
              </li>
            </ul>
          </div>
          <div class="mt-6 pt-4 border-t border-slate-800/50 flex justify-between items-center text-[10px] font-mono text-slate-500">
            <span>Primary Focus</span>
            <span class="text-purple-400 font-bold">Security & Test Isolation</span>
          </div>
        </div>

        <!-- Tech Card 3 -->
        <div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6 flex flex-col justify-between">
          <div>
            <div class="flex items-center gap-2.5 mb-4">
              <div class="w-8 h-8 rounded-lg bg-emerald-500/10 text-emerald-400 flex items-center justify-center border border-emerald-500/20">
                <span class="font-bold text-xs">PROD</span>
              </div>
              <h5 class="text-base font-extrabold text-white">운영 환경 기술 명세</h5>
            </div>
            <p class="text-base text-slate-400 leading-relaxed mb-6">
              최종 제품이 호스팅되는 클라우드 환경입니다. Edge 네트워크 캐싱과 SSL/DNS 자동 관리, 무중단 배포를 통해 승인 완료된 브랜치의 프로덕션 배포 파이프라인을 무중단으로 관리합니다.
            </p>
            <ul class="space-y-3.5 text-xs text-slate-300">
              <li class="flex items-start gap-2">
                <span class="text-emerald-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Vercel Deployment:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">GitHub 리포지토리 PR 및 메인 브랜치와 직결된 즉시 프리뷰(Instant Preview) 엔진.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-emerald-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">Edge Caching Network:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">지연 시간을 최소화하여 글로벌 전역에서 즉각적인 정적 리소스 로딩 속도 유지.</p>
                </div>
              </li>
              <li class="flex items-start gap-2">
                <span class="text-emerald-400 font-bold">▪</span>
                <div>
                  <strong class="text-white">HTTPS/SSL Security Policy:</strong>
                  <p class="text-xs text-slate-400 mt-0.5 leading-relaxed">자동 갱신되는 SSL 인증서와 엄격한 보안 오리진 설정을 통한 클라이언트 무한 보호.</p>
                </div>
              </li>
            </ul>
          </div>
          <div class="mt-6 pt-4 border-t border-slate-800/50 flex justify-between items-center text-[10px] font-mono text-slate-500">
            <span>Primary Focus</span>
            <span class="text-emerald-400 font-bold">Scalability & Seamless Deployment</span>
          </div>
        </div>

      </div>
    </section>

    <!-- Call to Action / Educational Summary -->
    <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800/80">
      <h4 class="text-base font-extrabold text-white mb-2">🎓 환경 분리가 보장하는 신뢰성</h4>
      <p class="text-base text-slate-400 leading-relaxed">
        이처럼 Vibe Coding 학습용 웹앱은 **개발(User)-실행(Jules Agent)-운영(Vercel Cloud)**으로 이어지는 3차적 물리 공간 분리를 통해, 각 환경 간 불필요한 결합을 원천 차단합니다. AI가 로컬 개발 컴퓨터를 더럽히거나 예상치 못한 스크립트를 원격에 바로 푸시할 걱정 없이, 완벽하게 통제되는 애자일 배포 생태계를 직접 체감해 보시기 바랍니다.
      </p>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'Environments',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const activeNode = ref('dev')

    const activeNodeName = computed(() => {
      if (activeNode.value === 'dev') return '개발 환경 (Development Environment)'
      if (activeNode.value === 'runtime') return '실행 환경 (Runtime Sandbox)'
      return '운영 환경 (Production Environment / Vercel)'
    })

    const activeNodeDescription = computed(() => {
      if (activeNode.value === 'dev') {
        return '개발 환경에서는 Vue 3 + Tailwind CSS 소스 코드를 편집하고, 모바일 기기를 활용하여 기획 요구사항을 GitHub Issue로 발제합니다. 사용자의 조작이 가상 환경의 Jules에게 신호를 전송하기 직전의 시점입니다.'
      }
      if (activeNode.value === 'runtime') {
        return '실행 환경은 AI 에이전트 Jules의 독립된 일터입니다. Node.js 패키지 종속성을 안전히 제어하고 npm run build, 테스트 등을 수행하여 소스 코드의 완성도를 빌드 차원에서 완벽히 검증한 후 다음 운영 환경으로 송출합니다.'
      }
      return '운영 환경은 전 세계 사용자가 학습 웹앱을 사용하는 호스팅 서버리스 망입니다. Vercel의 글로벌 Edge 서버 분산을 활용하여, 1초 안에 로딩되는 무중단 배포를 자동으로 진행하고 지속적인 실시간 버전을 갱신합니다.'
    })

    const getNodeBorderStyle = (nodeId) => {
      const isActive = activeNode.value === nodeId
      const color = props.stitchSettings.colorHex || '#ec4899'
      const thick = isActive ? `${(props.stitchSettings.thickness || 3) + 1}px` : '1px'
      const style = isActive ? (props.stitchSettings.style || 'dashed') : 'solid'
      const activeColor = isActive ? color : '#1e293b'

      return {
        borderWidth: thick,
        borderColor: activeColor,
        borderStyle: style,
        boxShadow: isActive ? `0 4px 15px rgba(0,0,0,0.1), 0 0 12px ${color}20` : 'none'
      }
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

    const getMcpPath = () => {
      return "M 10,12 C 150,0 450,24 590,12"
    }

    const getMcpDashArray = () => {
      const style = props.stitchSettings.style
      const gap = props.stitchSettings.gap || 6
      const thick = props.stitchSettings.thickness || 2

      if (style === 'dotted') {
        return `${thick} ${gap}`
      } else if (style === 'solid') {
        return 'none'
      } else {
        return `${gap * 1.5} ${gap}`
      }
    }

    const getMcpAnimationStyle = () => {
      const speed = props.stitchSettings.animSpeed || 0
      const color = props.stitchSettings.colorHex || '#ec4899'
      if (speed === 0) {
        return { stroke: color }
      }
      return {
        stroke: color,
        animation: `running-stitch ${speed}s linear infinite`
      }
    }

    return {
      activeNode,
      activeNodeName,
      activeNodeDescription,
      getNodeBorderStyle,
      customStitchLineStyle,
      getMcpPath,
      getMcpDashArray,
      getMcpAnimationStyle
    }
  }
}
</script>
