# Motion Performance — stay inside the frame budget

Distilled from the animation-performance skill (method in our own words). Use when an animation is janky, choppy, stutters, or drops frames; when choosing which property to animate; when deciding between CSS and JS animation on performance grounds; or when reaching for `will-change` or GPU layers.

## The frame budget
60fps is what the brain reads as fluid motion: **16.7ms per frame**. On a 120Hz screen — now most phones and many laptops — it is **8ms**. Design against the smaller number. For scale: a layout recalculation on a complex page can take over 100ms — a dozen missed frames, not one.

Two things decide whether you stay inside the budget:
1. **What you animate** — how much work each frame costs.
2. **Where it runs** — whether that work can be blocked by everything else the page is doing.

## What you animate
- **Animate `transform` and `opacity` only.** They skip layout and paint and run on the GPU. `clip-path` and measured height (accordions) are the documented exceptions. `padding`/`margin`/`height`/`width`/`top`/`left` trigger all three rendering steps.
- **Do not drive child transforms via a CSS variable on the parent** — it recalculates styles for all children. Set `transform` directly on the element.
- **Motion shorthands are hardware-accelerated from Motion 14.2.** Before 14.2, `x`/`y`/`scale` run on the main thread via `requestAnimationFrame` and drop frames under load — upgrade, or use the full transform string. Layout animations (`layout`, `layoutId`) run on the main thread in every version.

## Where it runs
- **CSS animations beat JS under load** — they run off the main thread; `requestAnimationFrame`-based animations stutter while the browser loads, scripts, or paints. Use CSS for predetermined motion, JS for dynamic and interruptible motion.
- **WAAPI** gives JS control with CSS performance (hardware-accelerated, interruptible, no library).
- **React: do not animate through state.** A state update per frame re-renders the tree. Drive the value with a ref / animation API and let React own only the start and end states.

## The symptom table
| Symptom | Likely cause | First check |
|---|---|---|
| Stutters only while the page loads | JS-driven animation on the main thread | Move it to CSS, or defer until load settles |
| Stutters on scroll | Layout/paint property animated, or scroll handler doing work per frame | Switch to `transform`/`opacity`; throttle the handler |
| Stutters on one device only | Frame budget halved (120Hz screen) or weak GPU | Design against 8ms; cap pixel ratio; reduce blur |
| Drops frames when many elements move | One animated property forcing style recalc on children | Set `transform` on each element directly, not via a parent variable |
| Smooth in isolation, janky in the product | Another system animating the same property | One system per property; remove the duplicate |

## `will-change`: two traps that look correct
- `will-change` is a hint, not a fix. It costs memory (a GPU layer per element) and helps only when the browser would otherwise re-rasterise every frame.
- **Do not put `will-change` on many elements, and never leave it on permanently.** Apply it just before the animation starts, remove it when the animation ends. An element that always has `will-change` is a permanent GPU layer for no benefit.

## Should you avoid JS animation?
No — but know the trade. CSS for predetermined motion (it survives load), JS for dynamic and interruptible motion (springs, gestures). If the motion must stay smooth while the page is busy, CSS wins. If it must respond to input mid-flight, JS wins.

## Diagnosis workflow
1. **Find what animates.** List every animated property and its driver (CSS, WAAPI, JS, library).
2. **Diagnose.** Reproduce the jank, then change one thing: property, thread, or trigger. Measure the frame time before and after — a fix without a measurement is a guess.
3. **Report.** The symptom, the cause, the fix, and the measured frame time. If the measurement cannot be reproduced, say so.
