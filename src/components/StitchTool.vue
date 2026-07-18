<template>
  <div class="bg-slate-800 border border-slate-700 rounded-xl p-6 shadow-xl relative overflow-hidden">
    <!-- Header Stitch Line -->
    <div
      class="absolute top-0 left-0 right-0 h-1"
      :style="stitchStyleObject"
    ></div>

    <div class="flex items-center gap-3 mb-6">
      <div
        class="p-2 rounded-lg bg-indigo-500/10 text-indigo-400 border border-indigo-500/20"
        :style="{ borderColor: colorHex }"
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"/>
          <path d="M12 6a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3z"/>
          <path d="M11.5 9a3.5 3.5 0 1 0 0 7 3.5 3.5 0 0 0 0-7z"/>
          <path d="M15 15.5l4.5 4.5"/>
        </svg>
      </div>
      <div>
        <h3 class="font-bold text-lg text-white flex items-center gap-2">
          Stitch Tool <span class="text-xs px-2 py-0.5 rounded-full bg-indigo-500/20 text-indigo-300 font-normal">스티치 도구</span>
        </h3>
        <p class="text-xs text-slate-400">디자인 커스텀 실시간 재봉기</p>
      </div>
    </div>

    <!-- Controls -->
    <div class="space-y-5">
      <!-- Stitch Color -->
      <div>
        <label class="text-xs font-semibold text-slate-400 block mb-2">실 색상 (Stitch Color)</label>
        <div class="grid grid-cols-4 gap-2">
          <button
            v-for="c in colors"
            :key="c.id"
            @click="selectColor(c.id)"
            class="px-2 py-1.5 rounded-lg text-xs font-medium border transition-all flex flex-col items-center gap-1"
            :class="[
              activeColor === c.id
                ? 'bg-slate-700/80 border-slate-500 text-white'
                : 'bg-slate-900/40 border-slate-800 text-slate-400 hover:border-slate-700'
            ]"
          >
            <span class="w-3.5 h-3.5 rounded-full border border-white/20" :style="{ backgroundColor: c.hex }"></span>
            <span>{{ c.name }}</span>
          </button>
        </div>
      </div>

      <!-- Stitch Style -->
      <div>
        <label class="text-xs font-semibold text-slate-400 block mb-2">바느질 종류 (Stitch Style)</label>
        <div class="grid grid-cols-2 gap-2">
          <button
            v-for="s in styles"
            :key="s.id"
            @click="selectStyle(s.id)"
            class="px-3 py-2 rounded-lg text-xs font-medium border text-left transition-all flex items-center justify-between"
            :class="[
              activeStyle === s.id
                ? 'bg-indigo-600/10 border-indigo-500 text-indigo-300'
                : 'bg-slate-900/40 border-slate-800 text-slate-400 hover:border-slate-700'
            ]"
          >
            <span>{{ s.name }}</span>
            <span class="text-slate-500 text-[10px]">{{ s.desc }}</span>
          </button>
        </div>
      </div>

      <!-- Border Thickness -->
      <div>
        <div class="flex justify-between items-center mb-1">
          <label class="text-xs font-semibold text-slate-400">실 두께 (Thickness)</label>
          <span class="text-xs font-mono text-slate-300">{{ thickness }}px</span>
        </div>
        <input
          type="range"
          min="1"
          max="6"
          v-model.number="thickness"
          class="w-full h-1.5 bg-slate-900 rounded-lg appearance-none cursor-pointer accent-indigo-500"
          @input="emitChanges"
        />
      </div>

      <!-- Gap / Interval -->
      <div>
        <div class="flex justify-between items-center mb-1">
          <label class="text-xs font-semibold text-slate-400">땀 길이 (Stitch Length)</label>
          <span class="text-xs font-mono text-slate-300">{{ stitchGap }}px</span>
        </div>
        <input
          type="range"
          min="2"
          max="16"
          v-model.number="stitchGap"
          class="w-full h-1.5 bg-slate-900 rounded-lg appearance-none cursor-pointer accent-indigo-500"
          @input="emitChanges"
        />
      </div>

      <!-- Animation Speed -->
      <div>
        <div class="flex justify-between items-center mb-1">
          <label class="text-xs font-semibold text-slate-400">흐르는 애니메이션 속도</label>
          <span class="text-xs font-mono text-slate-300">{{ animSpeed === 0 ? '정지' : animSpeed + 's' }}</span>
        </div>
        <input
          type="range"
          min="0"
          max="8"
          step="0.5"
          v-model.number="animSpeed"
          class="w-full h-1.5 bg-slate-900 rounded-lg appearance-none cursor-pointer accent-indigo-500"
          @input="emitChanges"
        />
      </div>
    </div>

    <!-- Live Preview Box -->
    <div class="mt-6 p-4 rounded-lg bg-slate-950/60 border border-slate-800">
      <div class="text-[10px] uppercase font-bold text-slate-500 mb-2 tracking-wider">미리보기 (Stitch Preview)</div>
      <div
        class="h-16 rounded-md flex items-center justify-center transition-all bg-slate-900/50"
        :style="previewBorderStyle"
      >
        <span class="text-xs text-slate-400 font-mono">STITCH DESIGN ACTIVATED</span>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed, watch, onMounted } from 'vue'

export default {
  name: 'StitchTool',
  emits: ['change'],
  setup(props, { emit }) {
    const colors = [
      { id: 'pink', name: '핫핑크', hex: '#ec4899' },
      { id: 'green', name: '네온그린', hex: '#22c55e' },
      { id: 'yellow', name: '옐로우', hex: '#eab308' },
      { id: 'blue', name: '스카이블루', hex: '#3b82f6' }
    ]

    const styles = [
      { id: 'dashed', name: '홈질 (Dashed)', desc: '- - -' },
      { id: 'dotted', name: '점선 (Dotted)', desc: '. . .' },
      { id: 'double', name: '이중 재봉 (Double)', desc: '===' },
      { id: 'solid', name: '박음질 (Solid)', desc: '───' }
    ]

    const activeColor = ref('pink')
    const activeStyle = ref('dashed')
    const thickness = ref(3)
    const stitchGap = ref(8)
    const animSpeed = ref(2)

    const colorHex = computed(() => {
      const found = colors.find(c => c.id === activeColor.value)
      return found ? found.hex : '#ec4899'
    })

    const selectColor = (id) => {
      activeColor.value = id
      emitChanges()
    }

    const selectStyle = (id) => {
      activeStyle.value = id
      emitChanges()
    }

    const stitchStyleObject = computed(() => {
      return {
        backgroundImage: `linear-gradient(90deg, ${colorHex.value} 50%, transparent 50%)`,
        backgroundSize: `${stitchGap.value * 2}px 100%`,
        height: `${thickness.value}px`
      }
    })

    // Compute border styling for preview box
    const previewBorderStyle = computed(() => {
      const color = colorHex.value
      const thick = `${thickness.value}px`
      const gap = `${stitchGap.value}px`

      let borderStyle = 'dashed'
      if (activeStyle.value === 'dotted') borderStyle = 'dotted'
      if (activeStyle.value === 'solid') borderStyle = 'solid'
      if (activeStyle.value === 'double') borderStyle = 'double'

      // Return object containing proper styles
      return {
        borderWidth: thick,
        borderColor: color,
        borderStyle: borderStyle,
        boxShadow: `0 0 10px ${color}1a`
      }
    })

    const emitChanges = () => {
      emit('change', {
        colorId: activeColor.value,
        colorHex: colorHex.value,
        style: activeStyle.value,
        thickness: thickness.value,
        gap: stitchGap.value,
        animSpeed: animSpeed.value
      })
    }

    onMounted(() => {
      emitChanges()
    })

    return {
      colors,
      styles,
      activeColor,
      activeStyle,
      thickness,
      stitchGap,
      animSpeed,
      colorHex,
      selectColor,
      selectStyle,
      stitchStyleObject,
      previewBorderStyle,
      emitChanges
    }
  }
}
</script>
