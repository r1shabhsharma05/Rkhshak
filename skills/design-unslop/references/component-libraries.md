# Component Libraries — lib-first (never hand-build what a library has)

Check these BEFORE writing custom UI. Use the library's component, styled to the direction. If a library has the component, do not hand-build it.

## Libraries (in check order)
| Library | What it is | Use for |
|---|---|---|
| **shadcn/ui** | Component framework, 61 primitives, added as source code via CLI (`npx shadcn@latest add`). Registry + community registries. | Base UI: buttons, dialogs, sheets, popovers, forms, tables, navigation. Check `npx shadcn@latest search` before writing custom markup. |
| **kokonutui** | 116 React components, shadcn registry. | Rich components beyond shadcn primitives — check the registry first. |
| **astrxy** | Meta's agent-ready design system, 174 components. | Large design-system builds; run its `doctor --built` gate. |
| **21st.dev** | 10,000+ React/Tailwind components, searchable with source. | Finding a specific component/pattern with source code. |
| **react-bits** | Animated React components. | Animated components (use sparingly — motion must explain something). |
| **GSAP** | Animation platform. | Choreographed sequences, ScrollTrigger. |
| **Lenis** | Smooth scroll engine. | Smooth scrolling (exactly one engine per site — Lenis OR Locomotive, never both). |

## Rules
- **Use existing components first.** Search the registry before writing custom UI. Check installed components first — don't import components that haven't been added, don't re-add ones already installed.
- **Style to the direction.** A library component takes the project's tokens (palette, type, radius, spacing) — it does not bring its own look. Every colour and font goes through a token.
- **No manual `z-index` on overlay components.** Dialog, Sheet, Popover, etc. handle their own stacking.
- **No sizing classes on icons inside components.** Components handle icon sizing.
- **One smooth-scroll engine.** Lenis or Locomotive, never both. Connect it correctly to GSAP ScrollTrigger, refresh after media/font changes, destroy on cleanup. Bypass under `prefers-reduced-motion`.
- **Three.js only with purpose.** Spatial depth, texture transition, displacement, or pointer response that materially supports the art direction — never as ornamental background noise.
