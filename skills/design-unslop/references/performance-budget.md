# Performance Budget — the numbers a design must meet

A beautiful design that loads slowly is not done. These are the budgets the design must meet. If the design can't meet them, the design changes — not the budget.

## Core Web Vitals (targets)
| Metric | Target | What it means |
|---|---|---|
| **LCP** (Largest Contentful Paint) | **≤ 2.5s** | The main content is visible. The hero image/text must not wait on slow assets. |
| **INP** (Interaction to Next Paint) | **≤ 200ms** | Taps/clicks feel instant. No long tasks blocking the main thread. |
| **CLS** (Cumulative Layout Shift) | **≤ 0.1** | Nothing jumps while loading. Every image/media has width + height (or aspect-ratio) reserved. |

## Design-side budgets
- **Fonts:** at most 2 families (3 with one outlier role). Use `font-display: swap`. Never block rendering on a font — the fallback must look acceptable. Subset fonts to the languages used.
- **Images:** every image has an explicit size + `loading="lazy"` below the fold + `decoding="async"`. Use modern formats (AVIF/WebP) with a fallback. Hero image is preloaded, not lazy. No image wider than its display size (serve responsive sizes).
- **Motion:** animations use `transform` and `opacity` only (never `width`, `height`, `top`, `left`). 60fps target — no jank. One smooth-scroll engine only. Pause/cancel animations offscreen or when the document is hidden.
- **JavaScript:** no render-blocking scripts for the first paint. Heavy effects (WebGL, particle systems) load after the first paint and have a static poster fallback. If JS fails, the static first frame is complete.
- **Blur/shadows:** bounded blur (large blurs are expensive). Shadows are neutral, soft, and small. No continuously animated offscreen content.

## How to check
- Measure on a real mid-range phone (not just a fast desktop) on a slow connection (throttled 4G). If it feels slow there, it is slow.
- Check LCP/INP/CLS with the browser's performance tools, at mobile + desktop.
- If a metric misses: the fix is in the design (smaller hero image, fewer fonts, less motion, reserved space) — not in asking the user to buy a faster phone.

## Rules
- **Never** trade performance for decoration. A gradient blob, a glass panel, or a particle field that blows the budget gets cut or simplified.
- **Reserve space** for everything that loads late (images, ads, embeds). Layout shift is a design bug.
- **Lazy is the default** below the fold. Eager is the exception (hero only).
