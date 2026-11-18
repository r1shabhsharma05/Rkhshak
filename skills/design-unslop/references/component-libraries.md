# Component Libraries — lib-first (never hand-build what a library has)

Check these BEFORE writing custom UI. Use the library's component, styled to the direction. If a library has the component, do not hand-build it.

## Libraries (in check order)
| Library | What it is | Use for |
|---|---|---|
| **shadcn/ui** | Component framework, 61 primitives, added as source code via CLI (`npx shadcn@latest add`). Registry + community registries. | Base UI: buttons, dialogs, sheets, popovers, forms, tables, navigation. Check `npx shadcn@latest search` before writing custom markup. |
| **kokonutui** | 116 React components, shadcn registry. | Rich components beyond shadcn primitives — check the registry first. |
| **astryx** | Meta's agent-ready design system, 174 components. | Large design-system builds; run its `doctor --built` gate. |
| **ui-motion-kit** | UI Motion Kit (HorizonX, commercial licence) — 50 animated, accessible React components: overlays, navigation, inputs, feedback, content, micro-interactions, transitions. Motion tokens in one source file. | Check FIRST on any design or animation build, before hand-building. Copy + adapt individual components; never redistribute the kit source. Fonts are not covered by its licence. |
| **pick-ui-library** | Decision table for picking a library by task (not a component source). | Motion → Motion (springs, layout, enter/exit); numbers → NumberFlow; charts → recharts (general) or Liveline (live/streaming); drag and drop → dnd kit; virtualization → Virtuoso. A simple hover or fade needs no library — plain CSS. |
| **landingfolio** | Reference gallery of real landing-page sections (hero, feature, pricing, testimonial, CTA, footer, header, content, logo-cloud, steps, demo) and whole pages. | Inspiration only. Fetch one category per section, open every screenshot before describing it, rebuild in your own code. Never paste a screenshot into the build, never lift the source page's copy, artwork, or fonts. The user picks from a shortlist; keep a collection of sections they liked, with their own words about why. |
| **21st.dev** | 10,000+ React/Tailwind components, searchable with source. | Finding a specific component/pattern with source code. |
| **react-bits** | Animated React components. | Animated components (use sparingly — motion must explain something). |
| **GSAP** | Animation platform. | Choreographed sequences, ScrollTrigger. |
| **Lenis** | Smooth scroll engine. | Smooth scrolling (exactly one engine per site — Lenis OR Locomotive, never both). |

## Rules
- **Use existing components first.** Search the registry before writing custom UI. Check installed components first — don't import components that haven't been added, don't re-add ones already installed.
- **Apply the locked system.** When a `design.md` exists, apply it to the component library (shadcn's design-system flow) instead of taking the library's defaults.
- **Pick the library by task, not by habit.** See the pick-ui-library row above for motion, charts, drag-and-drop, and virtualization.
- **Style to the direction.** A library component takes the project's tokens (palette, type, radius, spacing) — it does not bring its own look. Every colour and font goes through a token.
- **No manual `z-index` on overlay components.** Dialog, Sheet, Popover, etc. handle their own stacking.
- **No sizing classes on icons inside components.** Components handle icon sizing.
- **One smooth-scroll engine.** Lenis or Locomotive, never both. Connect it correctly to GSAP ScrollTrigger, refresh after media/font changes, destroy on cleanup. Bypass under `prefers-reduced-motion`.
- **Three.js only with purpose.** Spatial depth, texture transition, displacement, or pointer response that materially supports the art direction — never as ornamental background noise.
