<template>
  <div class="space-y-12">
    <!-- Header Hero -->
    <div class="relative rounded-3xl p-8 overflow-hidden bg-gradient-to-br from-indigo-950/40 to-slate-900/90 border border-slate-800">
      <div class="absolute top-0 left-0 right-0 h-0.5" :style="customStitchLineStyle"></div>

      <div class="max-w-4xl relative z-10">
        <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-semibold mb-4">
          🎯 SPEC-DRIVEN DEVELOPMENT (SDD)
        </span>
        <h2 class="text-3xl sm:text-4xl font-black text-white tracking-tight mb-3">
          Spec 기반 개발의 필요성과 방법론
        </h2>
        <p class="text-base text-slate-400 leading-relaxed max-w-3xl">
          개발을 빠르게 시작하려는 조급함이 실패의 가장 큰 원인입니다. AI 에이전트와 함께 협업하여 대규모 프로젝트를 성공으로 이끄는 비결은 코드가 아닌 **명확한 설계서(Specification)**를 먼저 작성하는 것입니다. 이 가이드는 Spec 기반 개발이 왜 절대적으로 필요한지, 어떻게 체계적으로 설계서를 작성하고 작업을 분해하는지, 그리고 에이전트가 사용하는 최신 기술과 역량(MCP, 도구 등)을 심도 있게 다룹니다.
        </p>
      </div>

      <!-- Live Color Dot Indicator -->
      <div class="absolute right-6 top-6 flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full animate-ping" :style="{ backgroundColor: stitchSettings.colorHex }"></span>
        <span class="text-[10px] font-mono font-bold tracking-wider text-slate-500 uppercase">Live Stitch Link</span>
      </div>
    </div>

    <!-- Section 1: Why Spec-Driven Development is Essential -->
    <section class="space-y-6">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">1. Spec 기반 개발이 필요한 이유</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        AI 에이전트는 기계적인 코드 작성 속도가 인간보다 수십 배 빠릅니다. 하지만, 방향성이 어긋난 코드를 빠른 속도로 작성하는 것은 결과적으로 해결하기 불가능한 더 큰 기술 부채와 스파게티 코드를 만들어냅니다. 인간 개발자는 설계자(Architect)로서 AI가 달성해야 할 정확한 스펙과 규칙을 사전에 제시해야 합니다.
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mt-6">
        <!-- Reason 1 -->
        <div
          class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
          :style="getStitchStyle('dashed')"
        >
          <div class="w-10 h-10 rounded-xl bg-pink-500/10 text-pink-400 flex items-center justify-center border border-pink-500/20 mb-4 group-hover:scale-110 transition-transform">
            <span>🛡️</span>
          </div>
          <h4 class="text-base font-extrabold text-white mb-2">분위기 코딩 붕괴 방지</h4>
          <p class="text-base text-slate-400 leading-relaxed">
            토대와 규격이 없는 코딩(Vibe Coding)은 초기 빌드 시에는 빠르게 작동하는 것처럼 보이지만, 한 시간만 지나도 서로 충돌하고 깨지는 불안정한 아키텍처를 유발합니다. 스펙은 에이전트의 충돌을 막는 단단한 토대가 됩니다.
          </p>
        </div>

        <!-- Reason 2 -->
        <div
          class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
          :style="getStitchStyle('dashed')"
        >
          <div class="w-10 h-10 rounded-xl bg-blue-500/10 text-blue-400 flex items-center justify-center border border-blue-500/20 mb-4 group-hover:scale-110 transition-transform">
            <span>🧠</span>
          </div>
          <h4 class="text-base font-extrabold text-white mb-2">기능 표류(Feature Drift) 차단</h4>
          <p class="text-base text-slate-400 leading-relaxed">
            AI 에이전트는 대화 세션이 바뀌면 이전의 사소한 설계 의도나 폴더 구조, 네이밍 규칙을 완전히 잊어버립니다. 스펙 문서(Memory Bank)를 지속적으로 읽히고 업데이트하여 세션 간 기억 단절과 아키텍처 오염을 예방합니다.
          </p>
        </div>

        <!-- Reason 3 -->
        <div
          class="bg-slate-900/50 p-6 rounded-2xl border transition-all duration-300 relative overflow-hidden group"
          :style="getStitchStyle('dashed')"
        >
          <div class="w-10 h-10 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center border border-emerald-500/20 mb-4 group-hover:scale-110 transition-transform">
            <span>⚡</span>
          </div>
          <h4 class="text-base font-extrabold text-white mb-2">개발 생산성 및 검증 비용 극대화</h4>
          <p class="text-base text-slate-400 leading-relaxed">
            명확하게 명세가 주어지면 에이전트는 한 번에 완벽한 무결점 코드를 생산할 수 있으며, 자가 수정 테스트 루프를 가동할 수 있습니다. 모호한 지시문으로 수십 번 리트라이하여 낭비되는 시간과 API 토큰 비용을 압도적으로 줄여줍니다.
          </p>
        </div>
      </div>
    </section>

    <!-- Section 2: Step-by-Step Methodology -->
    <section class="space-y-6">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">2. Spec 기반 개발 방법론 (Process)</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        스펙 기반 개발은 단순히 긴 문서를 작성하는 것에 그치지 않습니다. **아이디어 기획부터 설계, 작업 분해, 세분화된 구현**까지 이어지는 순환적이며 기민한 엔지니어링 프로세스입니다.
      </p>

      <!-- Step-by-step Interactive Flow Cards -->
      <div class="space-y-4">
        <div
          v-for="(step, idx) in steps"
          :key="idx"
          class="bg-slate-900/40 p-6 rounded-2xl border border-slate-800 flex flex-col md:flex-row gap-6 items-start justify-between"
        >
          <div class="flex gap-4 items-start max-w-3xl">
            <div
              class="w-10 h-10 rounded-xl font-mono font-black text-xs flex items-center justify-center flex-shrink-0"
              :style="{ backgroundColor: `${stitchSettings.colorHex}15`, color: stitchSettings.colorHex, border: `1px solid ${stitchSettings.colorHex}30` }"
            >
              0{{ idx + 1 }}
            </div>
            <div>
              <h5 class="text-base font-extrabold text-white flex items-center gap-2">
                {{ step.title }}
                <span class="text-xs font-mono text-slate-500 uppercase">[{{ step.alias }}]</span>
              </h5>
              <p class="text-base text-slate-400 leading-relaxed mt-2">
                {{ step.description }}
              </p>
            </div>
          </div>
          <div class="w-full md:w-auto flex-shrink-0 flex flex-wrap gap-1.5 justify-end">
            <span v-for="tag in step.tags" :key="tag" class="px-2 py-0.5 rounded bg-slate-950 border border-slate-800 text-[10px] text-slate-400 font-mono">
              {{ tag }}
            </span>
          </div>
        </div>
      </div>
    </section>

    <!-- Section 3: Agent Skills & Tools -->
    <section class="space-y-6">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">3. 에이전트 역량(Skills) 및 최신 도구</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        과거의 단순 완성(Autocomplete) 도구와 달리, 현대적인 AI 코딩 에이전트는 독립된 작업 환경에서 파일 관리, 셸 스크립트 실행, 로컬 빌드 및 원격 배포 파이프라인과 완벽히 호환되는 폭넓은 역량을 갖추고 동작합니다.
      </p>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Left: Agent Advanced Skills -->
        <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800 space-y-6">
          <h5 class="text-base font-extrabold text-white flex items-center gap-2">
            🤖 지능형 AI 에이전트 핵심 스킬
          </h5>
          <div class="space-y-4">
            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-indigo-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">문맥 복원 및 유지 (Context Bank Restoration)</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  프로젝트 루트 내에 배치된 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1 py-0.5 rounded">AGENTS.md</code>나 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1 py-0.5 rounded">progress-tracker.md</code> 파일을 먼저 탐색하여, 이전에 어떤 결정이 있었고 다음 단위 목표가 무엇인지 분석해 즉각적으로 작업 지점을 복원합니다.
                </p>
              </div>
            </div>

            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-indigo-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">빌드·테스트 자동 검증 및 자가 치유 (Self-Healing)</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  코드 수정 직후 내부 샌드박스에서 <code class="font-mono text-xs text-indigo-300 bg-slate-950 px-1 py-0.5 rounded">npm run build</code>나 린터 검사를 수행하여 TypeScript 컴파일 에러나 포맷 위반이 발생하면 로그를 역추적해 스스로 코드를 완벽히 수정합니다.
                </p>
              </div>
            </div>

            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-indigo-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">정밀 탐색 및 리팩토링 (Targeted Refactoring)</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  빌드 아티팩트(dist/, build/)를 건드리지 않고, 파일 구조를 깊이 탐색하여 원본 소스 코드만을 찾아서 정확하게 Git merge diff 방식으로 오염을 차단하며 스타일링과 로직을 점진적 개선합니다.
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Modern Tools & Protocol -->
        <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800 space-y-6">
          <h5 class="text-base font-extrabold text-white flex items-center gap-2">
            🔧 관련 도구 및 MCP 통신 아키텍처
          </h5>
          <div class="space-y-4">
            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-pink-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">MCP (Model Context Protocol)</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  앤트로픽(Anthropic)에서 정의한 개방형 통신 프로토콜입니다. 거대 언어 모델(LLM)이 로컬 파일 시스템 탐색, 터미널 명령어 호출, 기계 격리 샌드박스 접근, SQL DB 질의 등을 표준화된 API 규격을 통해 안전하게 제어하도록 지원합니다.
                </p>
              </div>
            </div>

            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-pink-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">Claude Code / Cursor / Windsurf</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  단순 프롬프트 대화창을 넘어 멀티 파일 전체 편집, 실시간 로컬 샌드박스 컴파일 검증, 깃 브랜치 관리 등 강력한 에이전틱 코딩 기능이 기본 빌트인되어 있는 최신 개발 IDE 및 CLI 인터페이스 도구입니다.
                </p>
              </div>
            </div>

            <div class="p-4 rounded-xl bg-slate-950/40 border border-slate-900 flex items-start gap-3">
              <span class="text-pink-400 font-bold mt-0.5">▪</span>
              <div>
                <strong class="text-white text-base font-extrabold">Vercel & Git-flow CI/CD Pipeline</strong>
                <p class="text-base text-slate-400 leading-relaxed mt-1">
                  에이전트가 완성한 코드가 Pull Request로 제출되면 배포 운영 서버인 Vercel에서 즉시 임시 프리뷰(Instant Preview) 망을 호스팅해 주고, 인간 개발자가 승인 및 머지하는 즉시 프로덕션 환경에 완전 자동 배포되는 완성도 높은 실무 파이프라인 도구입니다.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Interactive Interactive Spec Simulator Playground -->
    <section class="space-y-4">
      <div class="flex items-center gap-2 border-b border-slate-900 pb-3">
        <div class="w-2.5 h-6 rounded-full" :style="{ backgroundColor: stitchSettings.colorHex }"></div>
        <h4 class="text-lg font-extrabold text-white">4. 인터랙티브 Spec-to-Code 학습기 (SDD Sandbox)</h4>
      </div>
      <p class="text-base text-slate-400 leading-relaxed">
        구현할 기능의 구체적인 스펙을 아래 기획서 작성기에 텍스트로 적어보세요. 입력한 내용을 기반으로 AI 에이전트 Jules가 정확하고 깔끔하게 해석할 수 있는 **표준 단위 개발 스펙 파일(Spec Markdown)**을 실시간 생성하여 제공합니다.
      </p>

      <div class="bg-slate-900/60 border border-slate-800 rounded-2xl p-6 sm:p-8 space-y-6">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 items-stretch">
          <!-- Left Input Form -->
          <div class="space-y-4 flex flex-col justify-between">
            <div class="space-y-3">
              <div>
                <label class="text-[10px] font-mono font-bold tracking-wider text-slate-400 uppercase">Unit Number & Feature Name</label>
                <div class="grid grid-cols-4 gap-2 mt-1">
                  <input
                    type="text"
                    v-model="sandboxUnitNum"
                    class="p-2.5 rounded-xl bg-slate-950 border border-slate-800 text-xs font-mono text-indigo-300 text-center focus:outline-none focus:border-indigo-500"
                    placeholder="예: 05"
                  />
                  <input
                    type="text"
                    v-model="sandboxFeatureName"
                    class="p-2.5 rounded-xl bg-slate-950 border border-slate-800 text-xs text-white col-span-3 focus:outline-none focus:border-indigo-500"
                    placeholder="예: 사용자 알림 드롭다운 메뉴"
                  />
                </div>
              </div>

              <div>
                <label class="text-[10px] font-mono font-bold tracking-wider text-slate-400 uppercase">Goal (목적 및 의도)</label>
                <textarea
                  v-model="sandboxGoal"
                  rows="2"
                  class="w-full mt-1 p-2.5 rounded-xl bg-slate-950 border border-slate-800 text-xs text-slate-300 focus:outline-none focus:border-indigo-500"
                  placeholder="예: 대시보드 상단바 우측에 종 모양 아이콘을 클릭하면 미독 알림 리스트가 나오는 반응형 팝업 레이아웃을 생성한다."
                ></textarea>
              </div>

              <div>
                <label class="text-[10px] font-mono font-bold tracking-wider text-slate-400 uppercase">Implementation Details (상세 구현 사항)</label>
                <textarea
                  v-model="sandboxDetails"
                  rows="4"
                  class="w-full mt-1 p-2.5 rounded-xl bg-slate-950 border border-slate-800 text-xs text-slate-300 focus:outline-none focus:border-indigo-500"
                  placeholder="예: - Notifications.vue 컴포넌트를 작성하고 모의 JSON 데이터를 바인딩한다.&#10;- 클릭 시 열고 닫히는 토글을 구현하고 외부 영역 클릭 시 닫히도록 마운트 제어한다.&#10;- Tailwind CSS를 이용하여 테두리에 stitchSettings 테마를 주입한다."
                ></textarea>
              </div>
            </div>

            <button
              @click="resetSandbox"
              class="w-full py-2.5 rounded-xl bg-slate-950 hover:bg-slate-900 text-slate-400 hover:text-white text-xs font-bold border border-slate-800 transition-all flex items-center justify-center gap-1.5"
            >
              🔄 초기 입력 예시로 되돌리기
            </button>
          </div>

          <!-- Right Generated Code Output -->
          <div class="space-y-3 flex flex-col justify-between">
            <div class="flex items-center justify-between">
              <span class="text-[10px] font-mono font-bold tracking-wider text-slate-400 uppercase">📄 Generated Spec File (contents/specs/{{ sandboxSpecFilename }})</span>
              <button
                @click="copySpecCode"
                class="px-2.5 py-1 rounded bg-slate-950 hover:bg-slate-900 border border-slate-800 text-[10px] text-slate-300 font-bold transition-all"
                :style="{ borderColor: stitchSettings.colorHex }"
              >
                {{ copied ? '복사 성공! 👍' : '스펙 파일 복사' }}
              </button>
            </div>

            <div class="relative bg-slate-950 p-4 rounded-xl border border-slate-900 flex-grow">
              <pre class="font-mono text-[10px] sm:text-[11px] text-slate-300 overflow-x-auto leading-relaxed whitespace-pre max-h-[300px]">{{ generatedSpecMarkdown }}</pre>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Informational Conclusion Summary -->
    <div class="bg-slate-900/30 p-6 rounded-2xl border border-slate-800/80">
      <h4 class="text-base font-extrabold text-white mb-2">🎓 요약: "AI 개발의 진정한 주도권은 기획력에서 나옵니다"</h4>
      <p class="text-base text-slate-400 leading-relaxed">
        인간 개발자가 코드 타이핑과 사소한 에러 디버깅에 소모적인 시간을 보내는 시대는 지났습니다. 우리가 집중해야 할 영역은 **명확한 기술적 불변성(Invariant) 설계, 올바른 컴포넌트 경계 지정, 완벽한 인수 검증 체크리스트 작성**입니다. 스펙을 꼼꼼하게 작성하는 훈련을 통해, AI 에이전트를 가장 기민하게 활용하는 강력한 소프트웨어 아키텍트로 거듭나시기 바랍니다.
      </p>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'SpecDevelopment',
  props: {
    stitchSettings: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    const sandboxUnitNum = ref('05')
    const sandboxFeatureName = ref('사용자 알림 드롭다운 메뉴')
    const sandboxGoal = ref('대시보드 상단바 우측에 종 모양 아이콘을 클릭하면 미독 알림 리스트가 나오는 반응형 팝업 레이아웃을 생성한다.')
    const sandboxDetails = ref(`- Notifications.vue 컴포넌트를 작성하고 모의 JSON 데이터를 바인딩한다.
- 클릭 시 열고 닫히는 토글을 구현하고 외부 영역 클릭 시 닫히도록 마운트 제어한다.
- Tailwind CSS를 이용하여 테두리에 stitchSettings 테마를 주입한다.`)

    const copied = ref(false)

    const resetSandbox = () => {
      sandboxUnitNum.value = '05'
      sandboxFeatureName.value = '사용자 알림 드롭다운 메뉴'
      sandboxGoal.value = '대시보드 상단바 우측에 종 모양 아이콘을 클릭하면 미독 알림 리스트가 나오는 반응형 팝업 레이아웃을 생성한다.'
      sandboxDetails.value = `- Notifications.vue 컴포넌트를 작성하고 모의 JSON 데이터를 바인딩한다.
- 클릭 시 열고 닫히는 토글을 구현하고 외부 영역 클릭 시 닫히도록 마운트 제어한다.
- Tailwind CSS를 이용하여 테두리에 stitchSettings 테마를 주입한다.`
    }

    const sandboxSpecFilename = computed(() => {
      const num = sandboxUnitNum.value.trim() || 'NN'
      const rawName = sandboxFeatureName.value.trim().toLowerCase().replace(/[^a-z0-9\s가-힣]/g, '')
      const nameSlug = rawName.replace(/\s+/g, '-') || 'feature'
      return `${num}-${nameSlug}.md`
    })

    const generatedSpecMarkdown = computed(() => {
      const formattedDetails = sandboxDetails.value.trim()
      const color = props.stitchSettings.colorHex
      const style = props.stitchSettings.style
      const thick = props.stitchSettings.thickness

      return `# Unit ${sandboxUnitNum.value}: ${sandboxFeatureName.value}

## Goal
${sandboxGoal.value}

## Design
- 테두리: ${style} 스타일, 두께 ${thick}px, 컬러 헥스 ${color} 적용.
- 반응형: 모바일 화면에서는 풀화면 팝업, 데스크톱에서는 320px 우하단 레이아웃.
- 색상: bg-slate-900 서피스, text-slate-100 컬러, metadata는 text-slate-400 적용.

## Implementation

### Notifications Dropdown Component
${formattedDetails}

### Dynamic Integration
- App.vue 상단 네비게이션 헤더 바 우측 영역에 종형 SVG 아이콘 추가 및 상태 연결.

## Dependencies
- lucide-vue-next (아이콘 바인딩용)

## Verify when done
- [ ] 클릭 시 부드럽게 열고 닫히는지 검증
- [ ] 외부 화면 영역을 터치 및 클릭할 경우 정상 디스마운트 처리되는지 점검
- [ ] TypeScript 에러 및 빌드 오류 유무 확인 (npm run build 통과)
- [ ] 린터 검사 패스 및 모바일 반응형 디바이스 뷰포트 레이아웃 깨짐 검사`
    })

    const copySpecCode = () => {
      navigator.clipboard.writeText(generatedSpecMarkdown.value).then(() => {
        copied.value = true
        setTimeout(() => {
          copied.value = false
        }, 2000)
      }).catch(err => {
        console.error('Copy failed:', err)
      })
    }

    const steps = [
      {
        title: '요구사항 수립 및 초안 작성',
        alias: 'Specify',
        description: '아이디어를 무작정 코드로 치환하기 전, 기획의 명확한 의도와 해결 목표를 서술합니다. 입력값, 결과값, 핵심 사용자 흐름 및 구체적으로 무엇을 만들고 무엇을 만들지 않을 것인지(In/Out of Scope)를 문서로 확정합니다.',
        tags: ['markdown', 'project-overview.md', 'scope']
      },
      {
        title: '아키텍처 및 시스템 제약 정의',
        alias: 'Plan',
        description: '사용할 기술 스택 표를 정의하고, 시스템 경계가 되는 책임 폴더와 데이터 보관 규칙을 설계합니다. 특히 코드베이스가 결코 위배되어서는 안 되는 최소 4대 이상의 "불변 조건(Invariants)"을 명시하여 설계 일관성을 사전에 고정합니다.',
        tags: ['architecture.md', 'code-standards.md', 'invariants']
      },
      {
        title: '빌드 단위 분해 및 플랜 확정',
        alias: 'Tasks',
        description: '큰 비즈니스 요구사항을 에이전트가 집중도 있게 한번에 완성해 낼 수 있는 15분~1시간 남짓 분량의 독립된 단위(Unit NN)로 쪼갭니다. 보안, 아키텍처 의존성에 맞춰 순서를 영리하게 세우고, contents/specs/ 빌드플랜에 매핑합니다.',
        tags: ['00-build-plan.md', 'unit-sequencing', 'dependencies']
      },
      {
        title: '단위별 사양서 작성 및 에이전트 실행',
        alias: 'Implement',
        description: '구현 단계 직전에 해당 Unit의 개별 스펙 사양서를 생성합니다. 목표, 디자인 가이드라인, 구현 세부조항, 필요한 종속 라이브러리 및 완성 조건 검증 체크리스트를 전달하여 AI 에이전트가 샌드박스에서 완벽히 수정을 끝마치도록 제어합니다.',
        tags: ['spec-to-code', 'progress-tracker.md', 'verification']
      }
    ]

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
      sandboxUnitNum,
      sandboxFeatureName,
      sandboxGoal,
      sandboxDetails,
      sandboxSpecFilename,
      generatedSpecMarkdown,
      copySpecCode,
      copied,
      resetSandbox,
      steps,
      getStitchStyle,
      customStitchLineStyle
    }
  }
}
</script>

<style scoped>
/* running thread dynamic flow animation */
@keyframes running-stitch {
  0% {
    stroke-dashoffset: 24;
  }
  100% {
    stroke-dashoffset: 0;
  }
}
</style>
