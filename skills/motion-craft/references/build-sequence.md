# Build Sequence — turn a request for motion into an implementation

Distilled from the animate skill and Emil Kowalski's animation philosophy (method in our own words; values are the source's tables, cited not invented). Run the steps in order. Steps 1 and 2 gate everything.

## 1. Should this animate at all? (frequency gate)
| Frequency | Decision |
|---|---|
| 100+ times/day (keyboard shortcuts, command palette toggle) | **No animation. Ever.** Stop here. |
| Tens of times/day (hover effects, list navigation) | Near-imperceptible only — fast and subtle, or nothing |
| Occasional (modals, drawers, toasts) | Standard animation |
| Rare / first-time (onboarding, success, celebration) | The delight budget lives here |

**Keyboard-initiated actions are a disqualifier, not a judgment call.** If the request fails this gate, say so plainly and do not write the animation. Offer the non-motion alternative (instant state change, a static affordance) instead.

## 2. What is the purpose?
Name it in one of these words before continuing:
- **Feedback** — confirming the interface heard the user
- **Spatial consistency** — showing where something came from or went
- **State indication** — making a state change legible
- **Preventing a jarring change** — bridging content that would otherwise teleport
- **Explanation** — demonstrating how something works (marketing/onboarding only)
- **Delight** — allowed *only* at the rare/first-time tier

Cannot name it? Do not build it. "It looks cool" on a frequently-seen element is a reason to stop. Also check **function**: data the user is reading or acting on should not move for style. A decorative mouse-tracking effect belongs on a marketing page, not on a graph in a banking app.

## 3. Pick the tool — cheapest that works
Walk down; stop at the first that fits.
| Need | Tool |
|---|---|
| Hover, press, colour, a state toggle you control with a class or attribute | **CSS transition** |
| Entry animation on mount, no JS state | **CSS `@starting-style`** |
| Predetermined motion that must stay smooth while the page is busy loading | **CSS animation** (`transform`/`opacity` run on the compositor) |
| Programmatic control with CSS performance, no library | **WAAPI** (`element.animate()`) |
| Springs, layout animations, exit animations, gesture-driven values | **Motion** (motion.dev) |

CSS animations beat JS under load — on `transform`/`opacity` they run on the compositor, while `requestAnimationFrame`-based animation drops frames while the browser loads, scripts, or paints. Use CSS for predetermined motion, JS for dynamic and interruptible motion.

## 4. Pick the properties
- **`transform` and `opacity` only.** They skip layout and paint and run on the GPU. `width`/`height`/`margin`/`padding`/`top`/`left` trigger all three. (`clip-path` is the sanctioned fourth. `height` is tolerated only for accordions, where there is no transform equivalent.)
- **Never `scale(0)`.** Start from `scale(0.9–0.97)` + `opacity: 0`. Nothing in the real world appears from nothing.
- **`transform-origin` at the trigger** for popovers, dropdowns, menus, tooltips. **Modals are exempt** — they are not anchored to a trigger, so they stay centred.
- **Percentages in `translate()`** are relative to the element's own size — prefer them over hardcoded pixels.
- **Never drive a child's transform from a CSS variable on the parent** — it recalculates styles for every child. Set `transform` on the element directly.

## 5. Easing and duration — or a spring
**Easing**, in decision order:
| Situation | Easing |
|---|---|
| Entering or exiting | `ease-out` |
| Moving / morphing on screen | `ease-in-out` |
| Hover / colour change | `ease` |
| Constant motion (marquee, progress) | `linear` |
| Default | `ease-out` |

**Never `ease-in` on UI.** It starts slow, delaying the exact moment the user is watching. Built-in CSS easings are too weak — use strong curves (e.g. ease-out `cubic-bezier(0.23, 1, 0.32, 1)`, ease-in-out `cubic-bezier(0.77, 0, 0.175, 1)`, iOS-like drawer `cubic-bezier(0.32, 0.72, 0, 1)`). Need a curve that is not here? Take it from a published easing reference. Do not hand-roll one.

**Duration:**
| Element | Duration |
|---|---|
| Button press feedback | 100–160ms |
| Tooltips, small popovers | 125–200ms |
| Dropdowns, selects | 150–250ms |
| Modals, drawers | 200–500ms |
| Marketing / explanatory | Can be longer |

**UI animations stay under 300ms. Modals, drawers, sheets, and toasts are the documented exceptions.** A 180ms dropdown feels more responsive than a 400ms one.

**Reach for a spring instead** when the motion is drag with momentum, an element that should feel alive, a gesture the user can interrupt or reverse, or decorative mouse-tracking. See `physical-motion.md` for spring values.

## 6. Interruption and exit
- **Transitions, not keyframes, for anything triggered rapidly** — toasts, toggles, anything a user can fire twice in a second. Transitions retarget from the current value; keyframes restart from zero.
- **Springs for gestures**, because they carry velocity through an interruption.
- **Exit the way it entered.** A toast that slides in from the bottom leaves through the bottom. Symmetric paths are what make swipe-to-dismiss feel obvious.
- **Asymmetric timing where the user is deciding.** Slow on the deliberate phase (a hold-to-confirm press: 2s linear), snappy on the system response (release: 200ms ease-out).

## 7. Reduced motion and pointer gating
Ships with the animation, every time. Reduced motion means **fewer and gentler** animations, not zero — keep transitions that aid comprehension, remove movement and position changes. Under `prefers-reduced-motion: reduce`, drop transform-based motion (same timing, opacity only). Gate hover motion to `@media (hover: hover) and (pointer: fine)` — touch fires false hovers on tap.

## Never Ship (automatic blocks)
| Never | Instead |
|---|---|
| `transition: all` | Name the exact properties |
| `transform: scale(0)` entrance | `scale(0.95)` + `opacity: 0` |
| `ease-in` on a UI element | `ease-out` or a strong custom curve |
| Built-in `ease-out` on a deliberate animation | A strong custom curve |
| Animation on a keyboard shortcut or 100+/day action | No animation |
| UI duration over 300ms with no reason | 150–250ms |
| `transform-origin: center` on a trigger-anchored popover | `var(--transform-origin)` (modals exempt) |
| Keyframes on toasts, toggles, rapidly-triggered elements | CSS transitions |
| Animating `width`/`height`/`margin`/`padding`/`top`/`left` | `transform` / `opacity` |
| Ungated `:hover` motion | `@media (hover: hover) and (pointer: fine)` |
| Missing `prefers-reduced-motion` | Gentler variant, not zero |
| Everything entering at once | 30–80ms stagger |
