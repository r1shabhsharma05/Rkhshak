# Modern Web — platform patterns first (mandatory-first)

For any HTML/CSS/client-side JS task, consult the modern web guidance BEFORE writing code or adding a dependency. Web APIs evolve fast; training data contains obsolete patterns. This governs the **platform pattern** (native dialog vs JS modal, anchor positioning vs JS tooltip, container queries vs media queries), not the design or the component library. It does NOT override the design-pick rule (user picks from a shortlist of 3) or lib-first (check installed libraries first).

## When it applies
Modals/dialogs/popovers, tables, dark mode, anchor positioning, container queries, view transitions, scroll-driven animations, parallax/reveals, forms, validation, autofill, accessibility, custom selects, scrollbars, CWV (LCP, INP, CLS), content-visibility, fetch priority, image optimization, security, passkeys, HTML sanitization, web components, dates/timezones, built-in AI, WebAssembly, standard HTML/CSS/DOM in frameworks.

## When it does NOT apply
Backend (SQL, ORMs, API routes), infra/scripts (CI/CD, Docker, Actions, Python/Go, Git), tooling/trivial (Vite, tsconfig, ESLint, tests, copy/renames, third-party docs).

## How to use it
1. **Search** for the feature with a 2–5 word action-oriented query (`<verb> + <UI/platform object>`), e.g. `"light dismiss dialog"`, `"responsive data table"`. Omit framework/library names and app/domain nouns. Split multi-feature tasks into separate searches.
2. **Retrieve** the matching guide(s) and read them in full.
3. **Verify** the implementation against the guide before concluding — applicable guidance + fallbacks correctly applied, task fully satisfied.
4. **Disclose** in the final response which guides shaped the code (one bullet per guide, ≤75 words, with a short verbatim quote of the specific rule/gotcha) — or, if none applied, one sentence naming what was checked and why none applied.

## Rules
- Guides use vanilla HTML/CSS/JS — adapt them to the framework without dropping the modern feature.
- All guides assume **Baseline Widely available** features are safe without fallbacks. For features not Baseline widely available, follow the guide's fallback recommendations unless the user specified a custom browser support policy.
- Guard `window`/`HTMLElement` in SSR. Generate per-instance IDs/anchor-names. Keep `:root` and `@starting-style` top-level/unscoped.
- Source of truth: the modern-web-guidance guides (209 guides, 17 categories: accessibility, built-in-ai, css, forms, html, js, performance, privacy, pwa, security, ui-atoms, ui-behaviors, ui-components, ui-templates, user-experience, visual-design, wasm, webmcp).
