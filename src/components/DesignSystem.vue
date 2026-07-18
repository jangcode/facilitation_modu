<template>
  <div class="space-y-12">
    <!-- Intro Header -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-slate-900/90 to-indigo-950/20 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>
      <div class="max-w-3xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-pink-500/10 border border-pink-500/20 text-pink-300 text-xs font-semibold mb-4">
          🧵 STITCH DESIGN SPECIFICATION v1.0
        </span>
        <h3 class="text-2xl sm:text-3xl font-black text-white tracking-tight mb-2">
          스티치 디자인 시스템 가이드
        </h3>
        <p class="text-xs sm:text-sm text-slate-400 leading-relaxed">
          이 컴포넌트는 사이트 전체의 일관된 디자인 유지를 위한 실시간 토큰 가이드입니다. 왼쪽의 **Stitch Tool** 설정값에 맞춰 색상과 테두리가 실시간으로 연동되어 반응합니다.
        </p>
      </div>
    </div>

    <!-- Section 1: Color System & Tokens -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 bg-pink-500 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">1. 색상 체계 & 디자인 토큰</h4>
      </div>
      <p class="text-xs text-slate-400">배경색, 테두리, 포인트 스티치를 구성하는 주요 컬러 팔레트입니다.</p>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
        <!-- Palette 1 -->
        <div class="bg-slate-900/50 p-4 rounded-xl border border-slate-800 flex items-center gap-3">
          <div class="w-12 h-12 rounded-lg bg-slate-950 border border-slate-800 flex items-center justify-center text-xs font-bold font-mono text-slate-400 shadow-inner">#020617</div>
          <div>
            <h5 class="text-xs font-bold text-white">Slate 950 (Background)</h5>
            <p class="text-[10px] text-slate-500 font-mono">bg-slate-950</p>
          </div>
        </div>
        <!-- Palette 2 -->
        <div class="bg-slate-900/50 p-4 rounded-xl border border-slate-800 flex items-center gap-3">
          <div class="w-12 h-12 rounded-lg bg-slate-900 border border-slate-800 flex items-center justify-center text-xs font-bold font-mono text-slate-400 shadow-inner">#0F172A</div>
          <div>
            <h5 class="text-xs font-bold text-white">Slate 900 (Card Bg)</h5>
            <p class="text-[10px] text-slate-500 font-mono">bg-slate-900</p>
          </div>
        </div>
        <!-- Palette 3 -->
        <div class="bg-slate-900/50 p-4 rounded-xl border border-slate-800 flex items-center gap-3">
          <div class="w-12 h-12 rounded-lg bg-pink-500 border border-pink-400 flex items-center justify-center text-xs font-bold font-mono text-white shadow-inner" :style="{ backgroundColor: stitchSettings.colorHex, borderColor: stitchSettings.colorHex }">Live</div>
          <div>
            <h5 class="text-xs font-bold text-white">Stitch Live Color</h5>
            <p class="text-[10px] text-slate-500 font-mono" :style="{ color: stitchSettings.colorHex }">{{ stitchSettings.colorHex }}</p>
          </div>
        </div>
        <!-- Palette 4 -->
        <div class="bg-slate-900/50 p-4 rounded-xl border border-slate-800 flex items-center gap-3">
          <div class="w-12 h-12 rounded-lg bg-slate-950 border border-slate-800/80 flex items-center justify-center text-xs font-bold font-mono text-indigo-400 shadow-inner">#6366F1</div>
          <div>
            <h5 class="text-xs font-bold text-white">Indigo 500 (Theme)</h5>
            <p class="text-[10px] text-slate-500 font-mono">text-indigo-500</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Section 2: Typography Style Guide -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 bg-pink-500 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">2. 타이포그래피 (Typography)</h4>
      </div>
      <p class="text-xs text-slate-400">텍스트의 의미적 성격에 따른 일관된 크기 및 두께 표준입니다.</p>

      <div class="bg-slate-900/40 border border-slate-800 rounded-xl p-6 space-y-4">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 items-center border-b border-slate-800/50 pb-4">
          <div class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">Main Heading</div>
          <div class="md:col-span-2">
            <h1 class="text-2xl sm:text-3xl font-black text-white tracking-tight">Vibe Coding Study Note</h1>
            <code class="text-[10px] text-pink-400 bg-slate-950 px-1.5 py-0.5 rounded font-mono">text-2xl sm:text-3xl font-black text-white tracking-tight</code>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 items-center border-b border-slate-800/50 pb-4">
          <div class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">Section Title</div>
          <div class="md:col-span-2">
            <h2 class="text-lg font-extrabold text-white">바이브 코딩 핵심 패러다임</h2>
            <code class="text-[10px] text-pink-400 bg-slate-950 px-1.5 py-0.5 rounded font-mono">text-lg font-extrabold text-white</code>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 items-center">
          <div class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">Body / Small Desc</div>
          <div class="md:col-span-2">
            <p class="text-xs text-slate-400 leading-relaxed">인공지능 에이전트 Jules가 가상 샌드박스 환경에서 코드를 분석, 자동 설계, 구현 및 테스트를 자동 수행합니다.</p>
            <code class="text-[10px] text-pink-400 bg-slate-950 px-1.5 py-0.5 rounded font-mono">text-xs text-slate-400 leading-relaxed</code>
          </div>
        </div>
      </div>
    </section>

    <!-- Section 3: Interactive Stitch Patterns -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 bg-pink-500 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">3. 스티치 테두리 스타일 가이드 (Stitch Borders)</h4>
      </div>
      <p class="text-xs text-slate-400">재봉기 설정에 따라 반응형으로 바인딩되는 4대 테두리 스타일 및 클래스입니다.</p>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6">
        <!-- Dashed Box -->
        <div class="flex flex-col gap-2">
          <span class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">1. 홈질 (Dashed)</span>
          <div
            class="h-28 rounded-xl bg-slate-950 flex flex-col items-center justify-center border text-center p-3 relative overflow-hidden"
            :style="getStitchStyle('dashed')"
          >
            <span class="text-xs text-slate-300 font-extrabold">DASHED</span>
            <span class="text-[9px] text-slate-500 font-mono mt-1">border-style: dashed</span>
          </div>
        </div>

        <!-- Dotted Box -->
        <div class="flex flex-col gap-2">
          <span class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">2. 점선 (Dotted)</span>
          <div
            class="h-28 rounded-xl bg-slate-950 flex flex-col items-center justify-center border text-center p-3 relative overflow-hidden"
            :style="getStitchStyle('dotted')"
          >
            <span class="text-xs text-slate-300 font-extrabold">DOTTED</span>
            <span class="text-[9px] text-slate-500 font-mono mt-1">border-style: dotted</span>
          </div>
        </div>

        <!-- Double Box -->
        <div class="flex flex-col gap-2">
          <span class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">3. 이중 재봉 (Double)</span>
          <div
            class="h-28 rounded-xl bg-slate-950 flex flex-col items-center justify-center border text-center p-3 relative overflow-hidden"
            :style="getStitchStyle('double')"
          >
            <span class="text-xs text-slate-300 font-extrabold">DOUBLE</span>
            <span class="text-[9px] text-slate-500 font-mono mt-1">border-style: double</span>
          </div>
        </div>

        <!-- Solid Box -->
        <div class="flex flex-col gap-2">
          <span class="text-[11px] font-mono text-slate-500 uppercase tracking-wider">4. 박음질 (Solid)</span>
          <div
            class="h-28 rounded-xl bg-slate-950 flex flex-col items-center justify-center border text-center p-3 relative overflow-hidden"
            :style="getStitchStyle('solid')"
          >
            <span class="text-xs text-slate-300 font-extrabold">SOLID</span>
            <span class="text-[9px] text-slate-500 font-mono mt-1">border-style: solid</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Section 4: Buttons & Badges -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 bg-pink-500 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">4. 버튼 & 뱃지 컴포넌트</h4>
      </div>
      <p class="text-xs text-slate-400">사용자가 조작을 가하거나 정보를 상태별로 분류하기 위한 가이드라인입니다.</p>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- Buttons Guide -->
        <div class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800 space-y-4">
          <h5 class="text-xs font-mono text-slate-400 uppercase tracking-wider">Buttons (버튼 유형)</h5>

          <div class="flex flex-wrap gap-3">
            <button class="px-5 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-bold shadow-lg shadow-indigo-600/20 transition-all duration-300">
              Primary Button
            </button>
            <button class="px-5 py-2.5 rounded-xl bg-slate-950 hover:bg-slate-900 text-slate-300 hover:text-white text-xs font-bold border border-slate-800 transition-all duration-300">
              Secondary Button
            </button>
            <button
              class="px-5 py-2.5 rounded-xl text-xs font-bold border transition-all duration-300"
              :style="{ borderColor: stitchSettings.colorHex, color: stitchSettings.colorHex, backgroundColor: `${stitchSettings.colorHex}10` }"
            >
              Stitch Match Button
            </button>
          </div>

          <div class="pt-4 border-t border-slate-800/60 space-y-2">
            <div class="flex items-center justify-between text-[11px] text-slate-500">
              <span>Primary class:</span>
              <code class="text-slate-300 bg-slate-950 px-1 py-0.5 rounded text-[10px]">bg-indigo-600 hover:bg-indigo-500</code>
            </div>
            <div class="flex items-center justify-between text-[11px] text-slate-500">
              <span>Secondary class:</span>
              <code class="text-slate-300 bg-slate-950 px-1 py-0.5 rounded text-[10px]">bg-slate-950 border border-slate-800</code>
            </div>
          </div>
        </div>

        <!-- Badges Guide -->
        <div class="bg-slate-900/50 p-6 rounded-2xl border border-slate-800 space-y-4">
          <h5 class="text-xs font-mono text-slate-400 uppercase tracking-wider">Badges (뱃지 유형)</h5>

          <div class="flex flex-wrap gap-2">
            <span class="px-2.5 py-1 rounded bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-[11px] font-semibold">
              Vercel Hosted
            </span>
            <span class="px-2.5 py-1 rounded bg-pink-500/10 border border-pink-500/20 text-pink-300 text-[11px] font-semibold" :style="{ backgroundColor: `${stitchSettings.colorHex}10`, borderColor: `${stitchSettings.colorHex}30`, color: stitchSettings.colorHex }">
              Stitch Color Badge
            </span>
            <span class="px-2.5 py-1 rounded bg-emerald-500/10 border border-emerald-500/20 text-emerald-300 text-[11px] font-semibold">
              Success / Active
            </span>
            <span class="px-2.5 py-1 rounded bg-amber-500/10 border border-amber-500/20 text-amber-300 text-[11px] font-semibold">
              Warning
            </span>
          </div>

          <div class="pt-4 border-t border-slate-800/60 space-y-2">
            <div class="flex items-center justify-between text-[11px] text-slate-500">
              <span>Standard Badge class:</span>
              <code class="text-slate-300 bg-slate-950 px-1 py-0.5 rounded text-[10px]">bg-indigo-500/10 border border-indigo-500/20 text-indigo-300</code>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  name: 'DesignSystem',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
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
      customStitchLineStyle,
      getStitchStyle
    }
  }
}
</script>
