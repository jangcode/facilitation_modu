# Instructions for AI Coding Agents (including @jules)

This repository follows the **Stitch Design System** as defined in `DESIGN_SYSTEM.md`. When adding, modifying, or refactoring UI components or pages, you must strictly follow these principles to ensure visual and interactive consistency across the workspace.

## Core Directives

1. **Adhere to the Stitch Concept:**
   - Any new container, card, list item, or custom panel should support the dynamic border-style, border-width, and color variables driven by `stitchSettings`.
   - Use standard CSS variables or tailwind color extensions configured in `tailwind.config.js` (`stitch-pink`, `stitch-green`, etc.) when custom stitch-inspired highlights are needed.

2. **React to Live Theme Settings:**
   - Always ensure interactive layouts or pages can accept, inherit, or utilize the reactive settings returned by the global/parent `StitchTool.vue` component.
   - Do not hardcode borders, colors, or speeds when they can be bound to the reactive `stitchSettings`.

3. **Follow Component Patterns:**
   - **Cards:** Use `bg-slate-900/50` backgrounds, rounded corners, and customizable borders.
   - **Typography:** Use exact text sizing and spacing defined in `DESIGN_SYSTEM.md`.
   - **Buttons:** Keep secondary button borders subtle (`border-slate-800`), and primary buttons with standard shadows.

4. **Verify Build Stability:**
   - Always run `npm run build` after any visual or script changes to verify there are no linting, typescript, or build-time issues.
