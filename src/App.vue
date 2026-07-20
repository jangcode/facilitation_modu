<template>
  <div class="min-h-screen bg-slate-950 text-slate-100 flex flex-col font-sans selection:bg-indigo-500 selection:text-white">
    <!-- Header -->
    <header class="border-b border-slate-900 bg-slate-950/80 backdrop-blur-md sticky top-0 z-50 transition-all duration-300">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 min-h-16 py-3 md:py-0 flex flex-col md:flex-row items-center justify-between gap-3 md:gap-4">
        <div class="flex items-center gap-3">
          <div
            class="w-8 h-8 rounded-lg flex items-center justify-center font-black text-lg transition-all duration-500"
            :style="logoStyle"
          >
            V
          </div>
          <div>
            <h1 class="font-extrabold text-base text-white tracking-tight flex items-center gap-2">
              Vibe Coding Study Note
            </h1>
            <p class="text-[10px] text-slate-400 font-medium">바이브 코딩 학습 센터 & 실시간 시뮬레이터</p>
          </div>
        </div>

        <div class="flex flex-col sm:flex-row items-center gap-3 md:gap-4 w-full md:w-auto">
          <!-- View Toggle Tabs -->
          <div class="flex bg-slate-900 border border-slate-800 p-0.5 rounded-xl w-full sm:w-auto justify-between sm:justify-start">
            <button
              @click="currentTab = 'simulator'"
              class="px-2.5 sm:px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all whitespace-nowrap flex-1 sm:flex-none text-center"
              :class="currentTab === 'simulator' ? 'bg-indigo-600 text-white shadow-md shadow-indigo-600/10' : 'text-slate-400 hover:text-slate-200'"
            >
              시뮬레이터<span class="hidden sm:inline"> (Simulator)</span>
            </button>
            <button
              @click="currentTab = 'guide'"
              class="px-2.5 sm:px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all whitespace-nowrap flex-1 sm:flex-none text-center"
              :class="currentTab === 'guide' ? 'bg-indigo-600 text-white shadow-md shadow-indigo-600/10' : 'text-slate-400 hover:text-slate-200'"
            >
              실습 가이드<span class="hidden sm:inline"> (Guide)</span>
            </button>
            <button
              @click="currentTab = 'design'"
              class="px-2.5 sm:px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all flex items-center justify-center gap-1.5 whitespace-nowrap flex-1 sm:flex-none"
              :class="currentTab === 'design' ? 'bg-indigo-600 text-white shadow-md shadow-indigo-600/10' : 'text-slate-400 hover:text-slate-200'"
            >
              디자인 시스템
              <span class="w-1.5 h-1.5 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
            </button>
          </div>

          <div class="flex items-center gap-3 sm:gap-4">
            <a
              href="https://github.com"
              target="_blank"
              class="text-xs text-slate-400 hover:text-white flex items-center gap-1.5 px-3 py-1.5 bg-slate-900/60 border border-slate-800 rounded-lg hover:border-slate-700 transition-all"
            >
              <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2A10 10 0 0 0 2 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.9-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.9 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2z"/>
              </svg>
              GitHub Repo
            </a>

            <div class="px-2.5 py-1 rounded bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-[11px] font-semibold whitespace-nowrap">
              Vercel Hosted
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Container -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

      <!-- Tab 1: Simulator View -->
      <div v-if="currentTab === 'simulator'" class="space-y-8">
        <!-- Welcome Hero Section -->
        <section class="mb-8 relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/20 to-slate-900/60 border border-slate-800/80">
          <!-- Stitch line decorator top -->
          <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

          <div class="max-w-3xl relative z-10">
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-medium mb-4">
              <span>✨ Vue 3 + Tailwind CSS 기반 고성능 웹앱</span>
            </div>
            <h2 class="text-2xl sm:text-4xl font-black text-white tracking-tight mb-4">
              쉽고 빠른 AI 협업 모델, <br class="sm:hidden" />
              <span class="inline-block whitespace-nowrap text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 via-pink-400 to-amber-300">바이브 코딩(Vibe Coding)</span>
            </h2>
            <p class="text-sm sm:text-base text-slate-400 leading-relaxed mb-6">
              모바일 기기에서 터치 한 번으로 GitHub 이슈를 제안하고, AI 에이전트 <strong>Jules</strong>가 원격 가상 세션에서 완벽히 코드를 설계 및 배포하는 현대적이고 유기적인 애자일 개발 워크플로우를 학습합니다.
            </p>
            <div class="flex flex-wrap gap-3">
              <button
                @click="scrollToDiagram"
                class="px-5 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-bold shadow-lg shadow-indigo-600/20 transition-all duration-300 flex items-center gap-2"
              >
                다이어그램 보기
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                  <line x1="12" y1="5" x2="12" y2="19"/>
                  <polyline points="19 12 12 19 5 12"/>
                </svg>
              </button>
              <a
                href="#learn-more"
                class="px-5 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-300 hover:text-white text-xs font-bold border border-slate-800 transition-all duration-300"
              >
                개념 자세히 알아보기
              </a>
            </div>
          </div>

          <!-- Decorative stitched sewing pattern in back -->
          <div class="absolute right-0 bottom-0 top-0 w-1/3 opacity-10 hidden lg:block" :style="decorativeGridStyle"></div>
        </section>

        <!-- Content Grid: Sidebar (Stitch Tool) + Main (Workflow Diagram) -->
        <section class="grid grid-cols-1 lg:grid-cols-3 gap-8 mb-12" id="diagram-section">
          <!-- Left: Stitch Control Panel -->
          <div class="lg:col-span-1">
            <div class="sticky top-24">
              <StitchTool @change="handleStitchChange" />
            </div>
          </div>

          <!-- Right: Interactive Dynamic Diagram -->
          <div class="lg:col-span-2">
            <WorkflowDiagram :stitchSettings="stitchSettings" />
          </div>
        </section>

        <!-- Deep Educational Sections -->
        <section id="learn-more" class="border-t border-slate-900 pt-12 space-y-12">
        <div class="text-center max-w-2xl mx-auto mb-10">
          <h3 class="text-2xl font-black text-white tracking-tight">Vibe Coding 핵심 패러다임</h3>
          <p class="text-base text-slate-400 mt-2">이 시대 최고의 생산성을 발휘하는 인공지능 주도 개발(AI-Driven Development)의 핵심 기둥</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Card 1 -->
          <div
            class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition-all duration-300 relative overflow-hidden group"
            :style="getItemStyle"
          >
            <div class="w-10 h-10 rounded-xl bg-blue-500/10 text-blue-400 flex items-center justify-center border border-blue-500/20 mb-4 group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                <line x1="8" y1="21" x2="16" y2="21"/>
                <line x1="12" y1="17" x2="12" y2="21"/>
              </svg>
            </div>
            <h4 class="text-base font-extrabold text-white mb-2">모바일 제어 & 기민함</h4>
            <p class="text-base text-slate-400 leading-relaxed">
              기존의 무거운 로컬 개발 세팅에서 벗어나, 버스 안이나 카페 등 어디서나 스마트폰 GitHub 앱으로 기획을 마칩니다. AI와 유연하게 생각을 주고받는 진정한 기민함을 얻습니다.
            </p>
          </div>

          <!-- Card 2 -->
          <div
            class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition-all duration-300 relative overflow-hidden group"
            :style="getItemStyle"
          >
            <div class="w-10 h-10 rounded-xl bg-purple-500/10 text-purple-400 flex items-center justify-center border border-purple-500/20 mb-4 group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/>
                <polyline points="3.27 6.96 12 12.01 20.73 6.96"/>
                <line x1="12" y1="22.08" x2="12" y2="12"/>
              </svg>
            </div>
            <h4 class="text-base font-extrabold text-white mb-2">지능형 에이전트 Jules</h4>
            <p class="text-base text-slate-400 leading-relaxed">
              에이전트는 단순 오토컴플릿 도구가 아닙니다. 리포지토리 전체 분석, 빌드 명령어 설계, 테스트 케이스 생성 및 사전 실행 및 자가 수정을 통해 완결된 산출물을 직접 빌드합니다.
            </p>
          </div>

          <!-- Card 3 -->
          <div
            class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800 hover:border-slate-700 transition-all duration-300 relative overflow-hidden group"
            :style="getItemStyle"
          >
            <div class="w-10 h-10 rounded-xl bg-pink-500/10 text-pink-400 flex items-center justify-center border border-pink-500/20 mb-4 group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polygon points="12 2 2 7 12 12 22 7 12 2"/>
                <polyline points="2 17 12 22 22 17"/>
                <polyline points="2 12 12 17 22 12"/>
              </svg>
            </div>
            <h4 class="text-base font-extrabold text-white mb-2">Vercel 호스팅 & 즉시 배포</h4>
            <p class="text-base text-slate-400 leading-relaxed">
              PR 승인 즉시 Vercel의 고성능 Edge 네트워크에 무중단 서버리스 아키텍처로 전 세계 사용자에게 1초 만에 배포되어 빠른 검증 주기와 지속적인 릴리즈 피드백 루프를 구축합니다.
            </p>
          </div>
        </div>
      </section>
      </div>

      <!-- Tab 2: Vibe Coding Guide View -->
      <div v-else-if="currentTab === 'guide'">
        <!-- Vibe Coding Guide (Full Width) -->
        <VibeCodingGuide :stitchSettings="stitchSettings" />
      </div>

      <!-- Tab 3: Design System Spec View -->
      <div v-else-if="currentTab === 'design'">
        <!-- Design System Spec (Full Width) -->
        <DesignSystem :stitchSettings="stitchSettings" />
      </div>
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-900 mt-16 bg-slate-950/60 py-8 relative">
      <!-- Stitch line border top of footer -->
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4">
        <p class="text-xs text-slate-500">
          © 2026 Vibe Coding Case Study. All rights reserved. Created with <strong class="text-indigo-400 font-medium">Jules AI Agent</strong>.
        </p>
        <div class="flex gap-4">
          <span class="text-xs text-slate-500">Vercel & Vue.js Certified Architecture</span>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import StitchTool from './components/StitchTool.vue'
import WorkflowDiagram from './components/WorkflowDiagram.vue'
import DesignSystem from './components/DesignSystem.vue'
import VibeCodingGuide from './components/VibeCodingGuide.vue'

export default {
  name: 'App',
  components: {
    StitchTool,
    WorkflowDiagram,
    DesignSystem,
    VibeCodingGuide
  },
  setup() {
    const currentTab = ref('simulator')
    const stitchSettings = ref({
      colorId: 'pink',
      colorHex: '#ec4899',
      style: 'dashed',
      thickness: 3,
      gap: 8,
      animSpeed: 2
    })

    const handleStitchChange = (newSettings) => {
      stitchSettings.value = newSettings
    }

    const scrollToDiagram = () => {
      const el = document.getElementById('diagram-section')
      if (el) {
        el.scrollIntoView({ behavior: 'smooth', block: 'center' })
      }
    }

    // Styles reacting live to the custom stitch settings
    const logoStyle = computed(() => {
      const color = stitchSettings.value.colorHex
      return {
        backgroundColor: `${color}15`,
        borderColor: color,
        borderWidth: '2px',
        borderStyle: stitchSettings.value.style === 'solid' ? 'solid' : 'dashed',
        color: color,
        boxShadow: `0 0 10px ${color}20`
      }
    })

    const customStitchLineStyle = computed(() => {
      const color = stitchSettings.value.colorHex
      const gap = stitchSettings.value.gap
      const style = stitchSettings.value.style

      if (style === 'solid') {
        return { backgroundColor: color }
      }

      return {
        backgroundImage: `linear-gradient(90deg, ${color} 50%, transparent 50%)`,
        backgroundSize: `${gap * 2}px 100%`,
        height: `${stitchSettings.value.thickness || 2}px`
      }
    })

    const decorativeGridStyle = computed(() => {
      const color = stitchSettings.value.colorHex
      return {
        backgroundImage: `radial-gradient(${color} 1.5px, transparent 1.5px)`,
        backgroundSize: '24px 24px'
      }
    })

    const getItemStyle = computed(() => {
      const color = stitchSettings.value.colorHex
      const thick = `${stitchSettings.value.thickness || 2}px`
      let style = stitchSettings.value.style
      if (style === 'double') style = 'double'

      return {
        borderColor: color,
        borderWidth: thick,
        borderStyle: style,
        boxShadow: `0 4px 15px rgba(0,0,0,0.1), 0 0 10px ${color}10`
      }
    })

    return {
      currentTab,
      stitchSettings,
      handleStitchChange,
      scrollToDiagram,
      logoStyle,
      customStitchLineStyle,
      decorativeGridStyle,
      getItemStyle
    }
  }
}
</script>
