# Motion System — easing, durations, stagger (a system, not just "delete motion")

Pass 9 says delete motion by default and keep motion that explains something. This file is the system for the motion that stays: the easing curves, durations, and stagger rules, so every animation feels like it belongs to the same product.

## Easing (pick one family, use it everywhere)
| Curve | Use for | Values (cubic-bezier) |
|---|---|---|
| **Ease-out** (default) | Most entrances, reveals, hovers. Fast start, gentle stop. | `cubic-bezier(0.22, 1, 0.36, 1)` |
| **Ease-in-out** | Movements that go and return (toggles, drawers, modals). | `cubic-bezier(0.65, 0, 0.35, 1)` |
| **Spring** | Playful/elastic elements (only when the character is playful). | Spring physics, not a bezier — use the platform's spring. |
| **Linear** | Progress indicators, loading, anything continuous. Never for entrances. | `linear` |

Never use the default `ease` (it feels mushy) and never mix easing families on one screen.

## Durations (by distance + importance)
| Duration | Use for |
|---|---|
| **100–150ms** | Micro-feedback: button press, toggle, checkbox, hover. Feels instant. |
| **200–300ms** | Most transitions: fades, small slides, dropdowns, tooltips. The default range. |
| **400–600ms** | Larger movements: modals, drawers, page transitions, hero reveals. |
| **800ms+** | Only for choreographed hero sequences (GSAP). Never for UI feedback. |

Rule: the further something travels, the longer it takes — but never slower than the user can tolerate. If the user has to wait for an animation to finish before acting, it is too slow.

## Stagger (reveals)
- Stagger reveals by **40–80ms** per item, max **5 items** visible in one stagger. More than that feels like a queue.
- Reveal major headings word by word with a restrained stagger, then sequence supporting copy and media.
- Preserve an unsplit accessible name for staggered text. Hide decorative split words from assistive technology, never split links or meaningful inline markup, and keep the unsplit content visible without JavaScript.
- Never stagger a list the user needs to scan quickly (tables, search results, settings). Stagger is for storytelling, not for data.

## Choreography (GSAP)
- One idea per sequence. A hero intro is one sequence, not five competing ones.
- Navigation, primary message, and CTA are readable and usable BEFORE the animation completes.
- Use CSS for simple hover, focus, and tap states. Reserve ScrollTrigger for justified scrubbed or pinned sequences. Avoid multiple systems controlling the same property.
- Connect the smooth-scroll engine (Lenis or Locomotive — exactly one) correctly to GSAP ScrollTrigger, refresh measurements after media and font changes, and destroy it during cleanup.

## Rules
- **Motion explains something.** Every animation answers: what changed, where did it go, what happens next? If it doesn't explain, delete it.
- **Transform + opacity only.** Never animate `width`, `height`, `top`, `left`, or `transition: all`.
- **Reduced motion:** bypass smooth scrolling and scrubbed timelines under `prefers-reduced-motion: reduce`. Render final states immediately — never merely shorten the animation.
- **Static first frame:** the design is complete without JS, media playback, WebGL, or motion. Motion is additive, never required.
- **Pointer effects are additive.** Support touch, keyboard, coarse pointers, window blur, and visibility changes without leaving the interface incomplete.
