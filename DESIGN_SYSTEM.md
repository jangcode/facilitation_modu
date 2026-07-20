# 🧵 Stitch Design System (스티치 디자인 시스템)

이 문서는 **Vibe Coding Study Note**의 시각적 일관성을 유지하고, 새로운 컴포넌트나 페이지 추가 시 일관된 디자인 가이드라인을 제공하기 위해 만들어진 공식 디자인 시스템 문서입니다.

이 프로젝트는 전통적인 재봉틀/바느질(Sewing & Stitching)의 감성을 디지털화한 **'Stitch'** 디자인 컨셉을 기반으로 합니다. 동적이고 유동적인 실선/점선 데코레이터와 테두리 스타일을 활용하여 정교하면서도 트렌디한 느낌을 제공합니다.

---

## 🎨 1. 색상 체계 (Color System)

디자인 시스템의 기본 배경은 다크 테마(`slate-950`)이며, 스티치 효과를 돋보이게 하는 형광/파스텔 톤의 테마 컬러를 사용합니다.

| 색상 구분 | Tailwind 클래스 | 헥사 코드 (HEX) | 용도 및 설명 |
| :--- | :--- | :--- | :--- |
| **Primary (Dark)** | `bg-slate-950` | `#020617` | 메인 배경색, 어두운 무드를 조성 |
| **Secondary (Dark)** | `bg-slate-900` | `#0f172a` | 카드, 사이드바, 헤더 등 섹션 영역 배경색 |
| **Border Dark** | `border-slate-800` | `#1e293b` | 일반적인 컴포넌트 간 약한 구분 테두리 |
| **Accent Pink** | `text-stitch-pink` | `#ec4899` | 핫핑크 스티치, 하이라이트, 메인 포인트 컬러 |
| **Accent Green** | `text-stitch-green` | `#22c55e` | 네온그린 스티치, 실행 상태, 실시간 지표 표시 |
| **Accent Yellow** | `text-stitch-yellow` | `#eab308` | 옐로우 스티치, 경고, 알림, 수치 제어 |
| **Accent Blue** | `text-stitch-blue` | `#3b82f6` | 스카이블루 스티치, 정보 안내, 외부 링크 |

---

## 📐 2. 타이포그래피 (Typography)

가독성을 극대화하기 위해 서브헤더 및 레이블은 명확하고 굵게 지정합니다.

- **Main Heading / Hero Title**: `text-3xl sm:text-4xl font-black text-white tracking-tight`
- **Section Title**: `text-2xl font-black text-white tracking-tight`
- **Card / Group Title**: `text-base font-extrabold text-white`
- **Body / Standard Desc**: `text-base text-slate-400 leading-relaxed`
- **Subtitle / Small Desc**: `text-xs text-slate-400 leading-relaxed`
- **Metadata / Labels**: `text-[10px] sm:text-xs font-semibold tracking-wider uppercase`
- **Code / Value Label**: `font-mono text-xs text-slate-300 bg-slate-900`

---

## 🧵 3. 스티치 효과 가이드라인 (Stitch Guidelines)

스티치는 이 디자인 시스템의 **핵심 요소**입니다. 모든 주요 카드, 구분선, 버튼 장식에는 아래의 4가지 바느질 스타일 중 하나를 적용할 수 있어야 합니다.

### 3.1 스티치 스타일 속성
1. **홈질 (Dashed)**: `- - -` 형태의 점선 바느질. 가장 표준적이고 널리 사용됩니다.
2. **점선 (Dotted)**: `. . .` 형태의 점선. 좀 더 가볍고 세밀한 느낌을 줍니다.
3. **이중 재봉 (Double)**: `===` 형태의 이중 선. 중요도가 높은 테두리나 구분선에 적용합니다.
4. **박음질 (Solid)**: `───` 실선 형태의 정교한 박음질. 차분하고 깔끔한 마감에 적합합니다.

### 3.2 흐르는 스티치 애니메이션 (`running-stitch`)
사용자의 조작이나 실시간 시뮬레이션 상태일 때, 실이 흘러가는 듯한 `stroke-dashoffset` 애니메이션을 SVG 커넥터 및 테두리에 적용합니다.
- CSS 클래스: `animate-stitch` 또는 CSS 키프레임 `@keyframes running-stitch` 활용.

---

## 📦 4. 컴포넌트 규격 (Component Patterns)

### 4.1 카드 디자인 (Cards)
모든 카드는 기본적으로 `slate-900` 배경을 바탕으로 하고, 스티치 스타일 테두리가 감싸도록 제작합니다.
```html
<div class="bg-slate-900/50 p-6 rounded-2xl border border-stitch-pink/40 hover:border-stitch-pink transition-all duration-300 relative overflow-hidden group">
  <!-- Content here -->
</div>
```

### 4.2 버튼 디자인 (Buttons)
- **Primary Button**: 브랜드 인디고 컬러와 진한 그림자, 부드러운 스케일 업 애니메이션 효과.
  ```html
  <button class="px-5 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-bold shadow-lg shadow-indigo-600/20 transition-all duration-300">
    텍스트
  </button>
  ```
- **Outline / Secondary Button**: 테두리와 흐릿한 어두운 배경의 조화.
  ```html
  <button class="px-5 py-2.5 rounded-xl bg-slate-900 hover:bg-slate-800 text-slate-300 hover:text-white text-xs font-bold border border-slate-800 transition-all duration-300">
    텍스트
  </button>
  ```

### 4.3 뱃지 (Badges)
- 정보 강조용 마이크로 뱃지:
  ```html
  <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-500/10 border border-indigo-500/20 text-indigo-300 text-xs font-medium">
    ✨ 뱃지 내용
  </span>
  ```

---

## 💡 5. 확장 규칙 (Extensibility Rules)

새로운 컴포넌트나 페이지를 기획할 때는 반드시 **StitchTool.vue**의 테마 값(`stitchSettings`)을 상위 컨텍스트에서 주입(Prop, Provide/Inject, Pinia 등)받아 테두리 속성 및 SVG 커넥터에 동적으로 바인딩되도록 설계해야 합니다. 이를 통해 사용자가 좌측 실시간 재봉기 도구를 활용해 사이트 전체 테마를 동적으로 변경하는 인터랙티브 경험이 그대로 유지됩니다.
