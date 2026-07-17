<template>
  <div class="bg-slate-900 border border-slate-800 rounded-2xl p-8 relative overflow-hidden">
    <!-- Header title -->
    <div class="flex justify-between items-center mb-10">
      <div>
        <h4 class="text-white font-extrabold text-xl tracking-tight flex items-center gap-2">
          <span class="inline-block w-2 h-6 bg-indigo-500 rounded-full"></span>
          바이브 코딩 워크플로우 다이어그램
        </h4>
        <p class="text-xs text-slate-400 mt-1">이슈 등록부터 머지, Vercel 자동 배포까지 한눈에 확인하는 원격 협업 흐름</p>
      </div>
      <div class="flex items-center gap-1.5 px-3 py-1 bg-slate-950 border border-slate-800 rounded-full">
        <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
        <span class="text-[10px] text-slate-400 font-mono">LIVE STITCH PREVIEW</span>
      </div>
    </div>

    <!-- Steps Horizontal Layout for md+ screens, column for mobile -->
    <div class="grid grid-cols-1 md:grid-cols-5 gap-6 md:gap-4 relative z-10">

      <!-- Step 1: Issue Registration -->
      <div class="flex flex-col items-center">
        <div
          class="w-full bg-slate-950/60 p-5 rounded-xl border flex flex-col items-center text-center group hover:bg-slate-950/90 transition-all duration-300 relative"
          :style="getItemBorderStyle('dashed')"
        >
          <!-- Badge -->
          <span class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-slate-800 border border-slate-700 text-slate-300 font-bold text-[10px] px-2 py-0.5 rounded-full uppercase tracking-wider">Step 1</span>

          <div class="p-3 bg-blue-500/10 text-blue-400 rounded-xl mb-3 border border-blue-500/20 group-hover:scale-110 transition-transform">
            <!-- Smartphone Icon SVG -->
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="5" y="2" width="14" height="20" rx="2" ry="2"/>
              <line x1="12" y1="18" x2="12.01" y2="18"/>
            </svg>
          </div>

          <h5 class="text-sm font-bold text-white mb-1.5">모바일 이슈 등록</h5>
          <p class="text-[11px] text-slate-400 leading-relaxed">
            사용자는 휴대폰의 <strong class="text-blue-400 font-medium">GitHub 앱</strong>을 활용하여 요구사항이나 버그 이슈를 발제하고 <code class="text-slate-300 bg-slate-900 px-1 py-0.5 rounded text-[10px]">@jules</code> 에이전트에게 할당합니다.
          </p>
        </div>
      </div>

      <!-- Arrow Connector 1 -->
      <div class="flex items-center justify-center py-2 md:py-0">
        <div class="flex flex-col items-center justify-center w-full">
          <svg class="w-12 h-12 md:w-full md:h-12 text-slate-600 overflow-visible" viewBox="0 0 100 24" fill="none">
            <path
              :d="getConnectorPath()"
              stroke="currentColor"
              :stroke-width="stitchSettings.thickness || 2"
              :stroke-dasharray="getDashArray()"
              :style="getSvgAnimationStyle()"
              stroke-linecap="round"
            />
            <polygon points="94,8 100,12 94,16" :fill="stitchSettings.colorHex || '#ec4899'" class="hidden md:block" />
            <polygon points="46,20 50,24 54,20" :fill="stitchSettings.colorHex || '#ec4899'" class="block md:hidden" />
          </svg>
          <span class="text-[9px] font-mono text-slate-500 tracking-wider uppercase mt-1">이슈 감지</span>
        </div>
      </div>

      <!-- Step 2: Jules Agent Works -->
      <div class="flex flex-col items-center">
        <div
          class="w-full bg-slate-950/60 p-5 rounded-xl border flex flex-col items-center text-center group hover:bg-slate-950/90 transition-all duration-300 relative"
          :style="getItemBorderStyle('dashed')"
        >
          <!-- Badge -->
          <span class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-slate-800 border border-slate-700 text-slate-300 font-bold text-[10px] px-2 py-0.5 rounded-full uppercase tracking-wider">Step 2</span>

          <div class="p-3 bg-purple-500/10 text-purple-400 rounded-xl mb-3 border border-purple-500/20 group-hover:scale-110 transition-transform">
            <!-- Bot Icon SVG -->
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="11" width="18" height="10" rx="2"/>
              <circle cx="12" cy="5" r="2"/>
              <path d="M12 7v4"/>
              <line x1="8" y1="16" x2="8" y2="16"/>
              <line x1="16" y1="16" x2="16" y2="16"/>
            </svg>
          </div>

          <h5 class="text-sm font-bold text-white mb-1.5">Jules 원격 자동 구현</h5>
          <p class="text-[11px] text-slate-400 leading-relaxed">
            인공지능 에이전트 <strong class="text-purple-400 font-medium">Jules</strong>가 가상 샌드박스 환경에서 코드를 분석, 자동 설계, 구현 및 테스트를 자동 수행합니다.
          </p>
        </div>
      </div>

      <!-- Arrow Connector 2 -->
      <div class="flex items-center justify-center py-2 md:py-0">
        <div class="flex flex-col items-center justify-center w-full">
          <svg class="w-12 h-12 md:w-full md:h-12 text-slate-600 overflow-visible" viewBox="0 0 100 24" fill="none">
            <path
              :d="getConnectorPath()"
              stroke="currentColor"
              :stroke-width="stitchSettings.thickness || 2"
              :stroke-dasharray="getDashArray()"
              :style="getSvgAnimationStyle()"
              stroke-linecap="round"
            />
            <polygon points="94,8 100,12 94,16" :fill="stitchSettings.colorHex || '#ec4899'" class="hidden md:block" />
            <polygon points="46,20 50,24 54,20" :fill="stitchSettings.colorHex || '#ec4899'" class="block md:hidden" />
          </svg>
          <span class="text-[9px] font-mono text-slate-500 tracking-wider uppercase mt-1">PR & 빌드 요청</span>
        </div>
      </div>

      <!-- Step 3: Deployment & Review -->
      <div class="flex flex-col items-center">
        <div
          class="w-full bg-slate-950/60 p-5 rounded-xl border flex flex-col items-center text-center group hover:bg-slate-950/90 transition-all duration-300 relative"
          :style="getItemBorderStyle('dashed')"
        >
          <!-- Badge -->
          <span class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-slate-800 border border-slate-700 text-slate-300 font-bold text-[10px] px-2 py-0.5 rounded-full uppercase tracking-wider">Step 3</span>

          <div class="p-3 bg-emerald-500/10 text-emerald-400 rounded-xl mb-3 border border-emerald-500/20 group-hover:scale-110 transition-transform">
            <!-- Rocket/Cloud Icon SVG -->
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4.5 16.5c-1.5 1.25-2.5 3.5-2.5 3.5C5.5 21 8 19.5 9.5 18"/>
              <path d="M12 15l-3-3m0 0l3-3m-3 3h12"/>
              <path d="M16 3c1.5 1 4.5 4 4.5 4L12 15l-4-4L16 3z"/>
            </svg>
          </div>

          <h5 class="text-sm font-bold text-white mb-1.5">Vercel 호스팅 & 리뷰</h5>
          <p class="text-[11px] text-slate-400 leading-relaxed">
            자동으로 등록된 PR은 실시간으로 <strong class="text-emerald-400 font-medium">Vercel</strong> 클라우드에 배포됩니다. 사용자는 라이브 프리뷰를 보며 승인합니다.
          </p>
        </div>
      </div>

    </div>

    <!-- Stitch background decorative overlay grid -->
    <div class="absolute inset-0 pointer-events-none opacity-[0.02]" :style="gridPatternStyle"></div>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  name: 'WorkflowDiagram',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const getItemBorderStyle = (fallbackStyle) => {
      const color = props.stitchSettings.colorHex || '#ec4899'
      const thick = `${props.stitchSettings.thickness || 2}px`

      let borderStyle = props.stitchSettings.style || fallbackStyle
      if (borderStyle === 'double') borderStyle = 'double'

      return {
        borderWidth: thick,
        borderColor: color,
        borderStyle: borderStyle,
        boxShadow: `0 4px 20px rgba(0, 0, 0, 0.4), 0 0 15px ${color}15`
      }
    }

    const getConnectorPath = () => {
      // Horizontal wave for PC, straight down for mobile (which is handled inside component using responsive SVG scaling)
      return "M 0,12 C 30,0 70,24 100,12"
    }

    const getDashArray = () => {
      const style = props.stitchSettings.style
      const gap = props.stitchSettings.gap || 6
      const thick = props.stitchSettings.thickness || 2

      if (style === 'dotted') {
        return `${thick} ${gap}`
      } else if (style === 'solid') {
        return 'none'
      } else if (style === 'double') {
        // Double dashed look approximated in dash array
        return `${gap * 1.5} ${gap}`
      } else {
        // Default dashed
        return `${gap * 1.5} ${gap}`
      }
    }

    const getSvgAnimationStyle = () => {
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

    const gridPatternStyle = computed(() => {
      const color = props.stitchSettings.colorHex || '#ec4899'
      return {
        backgroundImage: `radial-gradient(${color} 1px, transparent 1px)`,
        backgroundSize: '20px 20px'
      }
    })

    return {
      getItemBorderStyle,
      getConnectorPath,
      getDashArray,
      getSvgAnimationStyle,
      gridPatternStyle
    }
  }
}
</script>
