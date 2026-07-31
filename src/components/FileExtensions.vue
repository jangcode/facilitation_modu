<template>
  <div class="space-y-12">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 to-slate-900/90 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🔍 CODE DNA & BUILD PIPELINE
        </span>
        <h2 class="text-3xl sm:text-4xl font-black text-white tracking-tight mb-3">
          파일 확장자로 읽는 기술 스택과 빌드 생태계
        </h2>
        <p class="text-base text-slate-400 leading-relaxed max-w-3xl">
          코드베이스에 포함된 파일들의 **확장자(Extension)**는 프로젝트의 DNA와 같습니다. 확장자를 살펴보는 것만으로도 어떤 프레임워크와 기술이 사용되었는지 파악할 수 있으며, 이 코드가 웹브라우저에서 직접 실행될 수 있는지 혹은 빌드 도구의 번들링 가공 단계가 필요한지, 그리고 로컬 컴퓨터에 어떤 런타임과 도구들이 사전에 설치되어야 하는지를 명확히 예측할 수 있습니다.
        </p>
      </div>

      <!-- Live Color Dot Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Link</span>
      </div>
    </div>

    <!-- Core Philosophy section -->
    <section class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div
        class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
        :style="getStitchStyle('dashed')"
      >
        <div class="w-10 h-10 rounded-xl bg-pink-500/10 text-pink-400 flex items-center justify-center border border-pink-500/20 mb-4 group-hover:scale-110 transition-transform">
          <span>🛠️</span>
        </div>
        <h4 class="text-base font-extrabold text-white mb-2">1. 기술 스택 예측 (DNA)</h4>
        <p class="text-base text-slate-400 leading-relaxed">
          파일 확장자는 사용 중인 프로그래밍 언어와 핵심 웹 프레임워크를 투영합니다. 예를 들어 <code class="font-mono text-xs text-pink-300 bg-slate-950 px-1.5 py-0.5 rounded">.vue</code>는 Vue 3 SFC 생태계를 의미하며, <code class="font-mono text-xs text-pink-300 bg-slate-950 px-1.5 py-0.5 rounded">.ts</code>는 안정적 타입 시스템 기반의 TypeScript 적용을 명확히 대변합니다.
        </p>
      </div>

      <div
        class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
        :style="getStitchStyle('dashed')"
      >
        <div class="w-10 h-10 rounded-xl bg-indigo-500/10 text-indigo-400 flex items-center justify-center border border-indigo-500/20 mb-4 group-hover:scale-110 transition-transform">
          <span>⚙️</span>
        </div>
        <h4 class="text-base font-extrabold text-white mb-2">2. 빌드 필요성 예측</h4>
        <p class="text-base text-slate-400 leading-relaxed">
          웹브라우저는 기본적으로 오직 순수한 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1.5 py-0.5 rounded">HTML/JS/CSS</code>만을 직접 이해하고 실행할 수 있습니다. 그 외의 고수준 확장자들은 브라우저 전달 전에 반드시 **트랜스파일링(Transpilation)** 및 **번들링(Bundling)**이라는 빌드 가공 단계가 필수적임을 뜻합니다.
        </p>
      </div>

      <div
        class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
        :style="getStitchStyle('dashed')"
      >
        <div class="w-10 h-10 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center border border-emerald-500/20 mb-4 group-hover:scale-110 transition-transform">
          <span>📦</span>
        </div>
        <h4 class="text-base font-extrabold text-white mb-2">3. 필요 도구 사전 파악</h4>
        <p class="text-base text-slate-400 leading-relaxed">
          특정 확장자가 보이면 이를 해석하고 변환하기 위해 어떤 개발 인프라가 갖춰져야 하는지 즉시 유추할 수 있습니다. 빌드 자동화를 주도하는 <code class="font-mono text-xs text-emerald-300 bg-slate-950 px-1.5 py-0.5 rounded">Node.js</code>, 의존성을 다운로드하는 패키지 매니저(<code class="font-mono text-xs text-emerald-300 bg-slate-950 px-1.5 py-0.5 rounded">npm/yarn/bun</code>), 초고속 모듈 결합 도구(<code class="font-mono text-xs text-emerald-300 bg-slate-950 px-1.5 py-0.5 rounded">Vite</code>) 등이 요구됩니다.
        </p>
      </div>
    </section>

    <!-- Interactive Extension Explorer -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">대화형 확장자 백과사전 (Interactive Extension Explorer)</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        프로젝트에서 자주 쓰이는 대표적인 파일 확장자 목록입니다. 각 확장자를 선택하여, 해당 확장자가 의미하는 기술 스택의 정의, 빌드가 필요한지 여부, 그리고 개발 단계에서 필수적으로 사용되는 소프트웨어 도구 및 실제 예시 코드를 상세히 탐색해 보세요.
      </p>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-stretch mt-6">
        <!-- Left Column: Extension List -->
        <div class="lg:col-span-1 space-y-2.5">
          <button
            v-for="ext in extensions"
            :key="ext.name"
            @click="activeExtension = ext"
            class="w-full text-left p-4 rounded-xl border text-xs flex items-center justify-between transition-all duration-300"
            :class="activeExtension.name === ext.name
              ? 'bg-slate-950 text-white font-bold'
              : 'bg-slate-900/30 border-slate-800 hover:border-slate-700 text-slate-400'"
            :style="activeExtension.name === ext.name ? { borderLeftWidth: '5px', borderLeftColor: stitchSettings.colorHex, borderColor: `${stitchSettings.colorHex}40` } : {}"
          >
            <div class="flex items-center gap-3">
              <span class="w-10 h-10 rounded-lg flex items-center justify-center font-mono font-black text-sm" :class="ext.badgeClass">
                {{ ext.name }}
              </span>
              <div class="flex flex-col">
                <span class="text-xs font-bold text-slate-300">{{ ext.fullName }}</span>
                <span class="text-[10px] text-slate-500 font-mono mt-0.5">Build Requirement: {{ ext.buildRequired ? '⚡ YES' : '❌ NO' }}</span>
              </div>
            </div>
            <span
              v-if="activeExtension.name === ext.name"
              class="w-1.5 h-1.5 rounded-full animate-ping"
              :style="{ backgroundColor: stitchSettings.colorHex }"
            ></span>
          </button>
        </div>

        <!-- Right Column: Detail Content and Live Info Box -->
        <div class="lg:col-span-2 flex flex-col justify-between space-y-6">
          <div class="bg-slate-900/80 p-6 rounded-2xl border border-slate-800 space-y-6 flex-grow">
            <!-- Active Header -->
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b border-slate-800/60 pb-4">
              <div class="flex items-center gap-3">
                <span class="w-12 h-12 rounded-xl flex items-center justify-center font-mono font-black text-base" :class="activeExtension.badgeClass">
                  {{ activeExtension.name }}
                </span>
                <div>
                  <h5 class="text-lg font-extrabold text-white">{{ activeExtension.fullName }}</h5>
                  <p class="text-xs text-slate-400">{{ activeExtension.category }}</p>
                </div>
              </div>

              <div>
                <span
                  class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-xs font-semibold border"
                  :class="activeExtension.buildRequired
                    ? 'bg-amber-500/10 border-amber-500/20 text-amber-300'
                    : 'bg-emerald-500/10 border-emerald-500/20 text-emerald-300'"
                >
                  <span class="w-1.5 h-1.5 rounded-full" :class="activeExtension.buildRequired ? 'bg-amber-400' : 'bg-emerald-400'"></span>
                  {{ activeExtension.buildRequired ? '빌드 필수 (Build Required)' : '즉시 브라우저 실행 가능' }}
                </span>
              </div>
            </div>

            <!-- Details Description Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <!-- Left: Description and Stack -->
              <div class="space-y-4">
                <div>
                  <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">🧬 사용 기술 / 프레임워크</span>
                  <p class="text-base text-slate-300 mt-1 leading-relaxed font-bold">
                    {{ activeExtension.techStack }}
                  </p>
                </div>
                <div>
                  <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase font-bold">⚙️ 빌드 가공이 왜 필요한가?</span>
                  <p class="text-xs text-slate-400 mt-1 leading-relaxed">
                    {{ activeExtension.buildReason }}
                  </p>
                </div>
              </div>

              <!-- Right: Required Tools -->
              <div class="space-y-4 bg-slate-950/40 p-4 rounded-xl border border-slate-800/40">
                <span class="text-[10px] font-mono font-bold tracking-wider text-indigo-400 uppercase">🔧 해석 및 빌드에 필요한 도구</span>
                <ul class="space-y-3 mt-1 text-xs">
                  <li v-for="tool in activeExtension.tools" :key="tool.name" class="flex items-start gap-2">
                    <span class="text-indigo-400 font-bold mt-0.5">▪</span>
                    <div>
                      <strong class="text-white font-bold">{{ tool.name }}</strong>
                      <p class="text-[10px] text-slate-500 leading-relaxed mt-0.5">{{ tool.desc }}</p>
                    </div>
                  </li>
                </ul>
              </div>
            </div>

            <!-- Code Example Box -->
            <div class="space-y-2">
              <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">📄 대표 코드 스니펫 예시 (Example Snippet)</span>
              <div class="relative bg-slate-950 p-4 rounded-xl border border-slate-900">
                <div class="absolute right-3 top-3 text-[10px] font-mono text-slate-600 uppercase">
                  {{ activeExtension.name }} Source
                </div>
                <pre class="font-mono text-xs text-slate-300 overflow-x-auto leading-relaxed whitespace-pre max-h-48">{{ activeExtension.snippet }}</pre>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Visual Build Pipeline (Vite Bundler Simulation Map) -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">현대적인 웹 빌드 파이프라인과 트랜스파일 시각화</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        고수준 기술 언어로 구성된 프로젝트 소스 파일들이 Vite와 같은 모듈 번들러를 관통하면서, 어떻게 경량화되고 최적화되어 웹브라우저가 곧장 읽을 수 있는 저수준 표준 리소스로 변형되어 최종 운영 서버(Vercel)에 배포되는지 그 흐름을 시각적으로 체득해 봅니다.
      </p>

      <div class="bg-slate-900/40 border border-slate-800 rounded-2xl p-6 sm:p-8 relative overflow-hidden">
        <div class="grid grid-cols-1 md:grid-cols-5 gap-4 items-center relative z-10">

          <!-- Source Files Box -->
          <div class="md:col-span-2 bg-slate-950/80 p-5 rounded-xl border border-slate-800 text-center space-y-3">
            <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">1. 소스 코드 입력 단계 (Source Code)</span>
            <h6 class="text-xs font-bold text-white">다양한 고수준 파일 혼재</h6>
            <div class="grid grid-cols-3 gap-2 mt-2">
              <div class="p-2 bg-slate-900 rounded-lg text-xs font-mono text-slate-300 border border-indigo-500/20">.vue</div>
              <div class="p-2 bg-slate-900 rounded-lg text-xs font-mono text-slate-300 border border-pink-500/20">.ts</div>
              <div class="p-2 bg-slate-900 rounded-lg text-xs font-mono text-slate-300 border border-amber-500/20">.css</div>
              <div class="p-2 bg-slate-900 rounded-lg text-xs font-mono text-slate-300 border border-slate-800 col-span-3">.json / .md / .js</div>
            </div>
            <p class="text-[11px] text-slate-500 leading-relaxed mt-2">
              가독성과 개발 생산성이 뛰어난 최적의 언어들이지만, 브라우저가 직접 컴파일할 수 없어 트랜스파일 가공 처리가 무조건 필요합니다.
            </p>
          </div>

          <!-- Bundler / Compiler Machine Box (Vite) -->
          <div class="md:col-span-1 flex flex-col items-center justify-center py-4">
            <div class="w-12 h-12 rounded-full flex items-center justify-center font-bold text-xs shadow-lg animate-bounce" :style="{ backgroundColor: stitchSettings.colorHex, color: '#000000', boxShadow: `0 0 15px ${stitchSettings.colorHex}40` }">
              Vite
            </div>
            <svg class="w-full h-8 text-slate-700 my-2 overflow-visible hidden md:block" viewBox="0 0 100 20" fill="none">
              <path
                d="M 0,10 L 100,10"
                stroke="currentColor"
                stroke-width="2"
                :stroke-dasharray="stitchSettings.style === 'solid' ? 'none' : '4 4'"
                :style="{ stroke: stitchSettings.colorHex }"
              />
              <polygon points="90,6 98,10 90,14" :fill="stitchSettings.colorHex" />
            </svg>
            <span class="text-[10px] font-mono text-slate-400 text-center">초고속 번들링 & 압축</span>
          </div>

          <!-- Pure Dist Output Box -->
          <div class="md:col-span-2 bg-slate-950/80 p-5 rounded-xl border border-emerald-500/20 text-center space-y-3">
            <span class="text-[10px] font-mono font-bold tracking-wider text-emerald-400 uppercase">2. 최종 산출물 단계 (Production Bundle)</span>
            <h6 class="text-xs font-bold text-white">표준 정적 파일로 완전 압축 (dist/)</h6>
            <div class="grid grid-cols-3 gap-2 mt-2">
              <div class="p-2 bg-emerald-500/10 text-emerald-300 rounded-lg text-xs font-mono border border-emerald-500/20">index.html</div>
              <div class="p-2 bg-emerald-500/10 text-emerald-300 rounded-lg text-xs font-mono border border-emerald-500/20">index-[hash].js</div>
              <div class="p-2 bg-emerald-500/10 text-emerald-300 rounded-lg text-xs font-mono border border-emerald-500/20">index-[hash].css</div>
            </div>
            <p class="text-[11px] text-slate-500 leading-relaxed mt-2">
              번들러의 변환 과정을 거쳐 오직 웹브라우저가 완전 무결하게 해독하고 로딩할 수 있는 기본 정적 웹 문서 세트로 완전하게 슬림화되었습니다.
            </p>
          </div>

        </div>

        <!-- Stitch Line connector at the bottom of the simulator map -->
        <div class="mt-6 pt-4 border-t border-slate-800/40 text-center">
          <span class="text-[10px] font-mono text-slate-500 uppercase tracking-wider">Stitched Build Flow Indicator</span>
          <svg class="w-full h-4 mt-2 overflow-visible" viewBox="0 0 600 10" fill="none">
            <line
              x1="0" y1="5" x2="600" y2="5"
              stroke="currentColor"
              :stroke-width="stitchSettings.thickness || 2"
              :stroke-dasharray="stitchSettings.style === 'solid' ? 'none' : '6 6'"
              :style="{ stroke: stitchSettings.colorHex }"
            />
          </svg>
        </div>
      </div>
    </section>

    <!-- Interactive Quiz / Summary Section -->
    <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800/80">
      <h4 class="text-base font-extrabold text-white mb-2">🎓 에이전트와 소통하기 전 꿀팁</h4>
      <p class="text-base text-slate-400 leading-relaxed">
        AI 에이전트 Jules에게 변경을 지시할 때, 프로젝트의 어떤 파일 확장자를 수정하고 결합해야 하는지 미리 머릿속에 설계해 보세요. 만약 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1 py-0.5 rounded">.vue</code> 파일을 수정했다면, Jules가 내부 실행 환경에서 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1 py-0.5 rounded">npm run build</code> 명령어를 실행하여 해당 수정을 완벽하게 검증하는 빌드 테스트를 필수 수행하게 됨을 이해할 수 있습니다.
      </p>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'FileExtensions',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const extensions = [
      {
        name: '.vue',
        fullName: 'Vue 3 Single File Component',
        category: '프론트엔드 프레임워크 컴포넌트',
        buildRequired: true,
        badgeClass: 'bg-emerald-500/15 text-emerald-400 border border-emerald-500/25',
        techStack: 'Vue 3 SFC / Composition API / Script Setup',
        buildReason: '웹브라우저는 <template>, <script>, <style>이 하나의 파일 안에 결합된 복합 파일 구조(.vue)를 기본 해석하지 못합니다. 따라서 빌드 단계에서 각 코드를 순수한 JS 모듈 및 CSS 리소스로 분리 변형해 주어야 합니다.',
        tools: [
          { name: 'Vite & @vitejs/plugin-vue', desc: 'Vue SFC 파일을 파싱하고 핫 리로딩(HMR) 및 JS 컴파일을 관장합니다.' },
          { name: 'vue-tsc', desc: '템플릿 내부의 TypeScript 구문 오류 및 타입 체크를 완벽히 정적 분석합니다.' }
        ],
        snippet: `<script setup>
import { ref } from 'vue'
const count = ref(0)
const increment = () => count.value++
<\/script>

<template>
  <button @click="increment">Click count: {{ count }}</button>
</template>

<style scoped>
button { @apply px-4 py-2 rounded bg-indigo-600 text-white; }
</style>`,
      },
      {
        name: '.ts',
        fullName: 'TypeScript Source Code',
        category: '정적 타입 프로그래밍 언어',
        buildRequired: true,
        badgeClass: 'bg-blue-500/15 text-blue-400 border border-blue-500/25',
        techStack: 'TypeScript / ES6+ Javascript with Static Types',
        buildReason: 'TypeScript는 엄격한 타입 안정성을 위해 인간이 보는 컴파일 전용 명세입니다. 런타임 표준 자바스크립트 엔진(V8 등)은 타입 문법(interface, type, generics 등)을 해석하지 못하므로, 타입 어노테이션을 전부 깨끗하게 지우고 순수한 JS 코드로 트랜스파일하는 과정이 동반되어야 합니다.',
        tools: [
          { name: 'tsc (TypeScript Compiler)', desc: 'TypeScript 파일을 타입 검사하고 자바스크립트로 변환하는 원조 컴파일러입니다.' },
          { name: 'esbuild / SWC', desc: 'Vite 내부에서 초고속으로 타입 체크 없이 문법만을 먼저 초고속 트랜스파일링 해줍니다.' }
        ],
        snippet: `interface User {
  id: number;
  name: string;
  role: 'admin' | 'user';
}

export function getUserGreeting(user: User): string {
  return \`Welcome back, \${user.name}! Role: \${user.role}\`;
}`,
      },
      {
        name: '.js',
        fullName: 'JavaScript File',
        category: '웹 표준 클라이언트 프로그래밍 언어',
        buildRequired: false,
        badgeClass: 'bg-yellow-500/15 text-yellow-400 border border-yellow-500/25',
        techStack: 'EcmaScript 표준 JavaScript / Node.js 모듈',
        buildReason: '최신 브라우저는 자바스크립트 파일을 기본적으로 실행할 수 있습니다. 단, 오래된 하위 브라우저 호환성을 유지하거나 여러 개의 JS 조각 파일들을 하나로 밀착하여 네트워킹 속도를 향상시키기 위해 코드 압축(Minify) 및 번들 결합(Bundle) 빌드가 대개 적용됩니다.',
        tools: [
          { name: 'Node.js Runtime', desc: '서버 환경 및 터미널 상에서 자바스크립트 스크립트를 기계어 레벨로 즉시 파싱하고 실행하는 인터프리터 런타임입니다.' },
          { name: 'Terser / Terser Plugin', desc: '자바스크립트 변수명을 극단적으로 줄이고 불필요한 줄바꿈을 제거해 파일 용량을 최적화합니다.' }
        ],
        snippet: `// Entry point main.js
import { createApp } from 'vue'
import App from './App.vue'
import './style.css'

createApp(App).mount('#app')`,
      },
      {
        name: '.css',
        fullName: 'Cascading Style Sheets',
        category: '스타일시트 디자인 리소스',
        buildRequired: false,
        badgeClass: 'bg-indigo-500/15 text-indigo-400 border border-indigo-500/25',
        techStack: 'CSS3 / Tailwind CSS Directive / Utility-First Styles',
        buildReason: '기본적인 CSS는 브라우저가 온전히 읽어 냅니다. 하지만 Tailwind CSS 같은 유틸리티 우선 프레임워크나 최신 중첩 문법을 사용할 때는 소스 코드에서 쓰인 @tailwind 지시문을 분석하여 실제 브라우저 호용 스타일로 확장 변환하는 PostCSS 빌드 단계가 관여해야 합니다.',
        tools: [
          { name: 'PostCSS', desc: 'CSS 문법에 플러그인들을 적용해 하위 호환 벤더 프리픽스를 자동으로 붙이고 번들링을 돕습니다.' },
          { name: 'Tailwind CSS CLI', desc: '작성된 HTML 및 Vue 소스 코드를 빠르게 탐색하여 사용된 클래스 명만 골라 최소 크기의 CSS 파일로 빌드해 냅니다.' }
        ],
        snippet: `@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  body {
    @apply bg-slate-950 text-slate-100;
  }
}`,
      },
      {
        name: '.json',
        fullName: 'JavaScript Object Notation',
        category: '구조화 데이터 인터체인지 포맷',
        buildRequired: false,
        badgeClass: 'bg-pink-500/15 text-pink-400 border border-pink-500/25',
        techStack: '데이터 규격 명세 / package.json 의존성 지도',
        buildReason: 'JSON 파일은 단순히 텍스트 형태의 범용 데이터 포맷으로, 어떠한 컴파일이나 변환 없이 언어 불문 곧바로 읽어 메모리에 객체 형태로 로드할 수 있습니다. 빌드 시에는 단순히 번들러에 의해 정적 자산으로 포함되거나 JS 모듈 내부에 인라인 통합되기도 합니다.',
        tools: [
          { name: 'NPM (Node Package Manager)', desc: 'package.json 내부를 해독하여 어떤 외부 라이브러리 목록들을 내려받아야 하는지 의존성 트리를 해독하고 설치합니다.' }
        ],
        snippet: `{
  "name": "vibe-coding-study",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "vite",
    "build": "vite build"
  }
}`,
      },
      {
        name: '.md',
        fullName: 'Markdown Document',
        category: '경량 구조 기록 문서',
        buildRequired: false,
        badgeClass: 'bg-purple-500/15 text-purple-400 border border-purple-500/25',
        techStack: 'README.md / AGENTS.md 가이드 지침 / 기획서 문서',
        buildReason: '마크다운은 개발자와 AI가 읽고 쓰는 자연어 기록지입니다. 브라우저가 화면에 예쁘게 그리기 위해서는 마크다운 원문을 HTML 태그(<p>, <h1> 등)로 동적 렌더링하는 Markdown 파서 및 컴포넌트 변환 처리(SFC 연계 등)가 결합될 때만 뷰어로 노출됩니다.',
        tools: [
          { name: 'Markdown Parsers (marked, mdit)', desc: '마크다운 기호들을 실시간 HTML 스트링 구조로 파싱 변환해 주는 라이브러리입니다.' }
        ],
        snippet: `# 🧵 Stitch Design System

이 문서는 **Vibe Coding Study Note**의 시각적 일관성을 유지하기 위해 제작된 공식 문서입니다.

- **Primary**: bg-slate-950
- **Accent**: text-stitch-pink`,
      }
    ]

    const activeExtension = ref(extensions[0])

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

    return {
      extensions,
      activeExtension,
      getStitchStyle,
      customStitchLineStyle
    }
  }
}
</script>

<style scoped>
/* Keyframes for stitch running thread flow simulation */
@keyframes running-stitch {
  0% {
    stroke-dashoffset: 24;
  }
  100% {
    stroke-dashoffset: 0;
  }
}
</style>
