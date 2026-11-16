# Animation Techniques — 20 ways to make beautiful AI animations

Concrete animation techniques with values. This file extends `motion-system.md` (easing, durations, stagger) with 20 specific techniques. Use the values as given — they are the technique, not a starting point.

## The 20 techniques
| # | Technique | Value / rule |
|---|---|---|
| 1 | **Ease-out for entrances** | Elements enter with ease-out (`cubic-bezier(0.22, 1, 0.36, 1)`). Fast start, gentle stop. The default for every entrance. |
| 2 | **Dropdowns at 150–250ms** | A dropdown opens in 150–250ms. Faster feels broken, slower feels laggy. |
| 3 | **Stagger list rows by 30ms** | List rows reveal with a 30ms stagger per row. Subtle, not a cascade. Max 5 rows in one stagger. |
| 4 | **Scale to 0.97 on press** | A pressed button scales to 0.97. One press cue, not a bounce. |
| 5 | **Stretch moving knobs 12%** | A dragged knob/slider stretches 12% in the direction of movement. It feels physical, not digital. |
| 6 | **Stagger as details settle** | When a screen loads, stagger the details (not the headline) as they settle — 40–80ms apart. The headline is already there. |
| 7 | **Arcs for object movement** | A moving object follows an arc, not a straight line. Arcs feel natural; straight lines feel robotic. |
| 8 | **Pulse to confirm success** | A successful action gets one gentle pulse (scale 1.0 → 1.05 → 1.0, 200ms). One pulse, not a loop. |
| 9 | **Ease-in-out for moves** | An element that moves and returns (toggle, drawer, modal) uses ease-in-out (`cubic-bezier(0.65, 0, 0.35, 1)`). |
| 10 | **Start popovers at 0.95** | A popover/tooltip starts at scale 0.95 + opacity 0, and animates to 1.0. It grows from its trigger, not from nowhere. |
| 11 | **Enter from the trigger** | A menu, popover, or panel enters from the element that opened it (its trigger). The user sees where it came from. |
| 12 | **Exit to the trigger** | A menu, popover, or panel exits back toward its trigger. The user sees where it went. |
| 13 | **No bounce on everyday UI** | Everyday UI (buttons, toggles, menus) never bounces. Bounce is for playful moments only — and only when the character is playful. |
| 14 | **Don't tween while held** | While the user holds/drags an element, don't animate it (no tween). The element follows the finger directly. Animate only on release. |
| 15 | **Make exits 20% shorter** | An exit animation is 20% shorter than the matching entrance. Exits should feel quick — the user is leaving, not arriving. |
| 16 | **Overlap old & new states** | During a transition, the old state and the new state overlap briefly (crossfade). No blank gap, no flash. |
| 17 | **Masks for reveals & colour** | Reveal content with a mask (clip-path) instead of a fade. A mask reveal feels physical; a fade feels like a PowerPoint. |
| 18 | **Crossfade icons + blur** | When an icon changes, crossfade it with a slight blur (not a hard swap). The blur hides the swap. |
| 19 | **Rubber band past bounds** | When a scroll/drag passes its bound, it stretches past it and springs back (rubber band). The overshoot is small and quick. |
| 20 | **Reuse the same layoutId** | When an element moves between states/screens, reuse the same layout id (Framer Motion `layoutId`). The element animates from its old position to its new one — it doesn't disappear and reappear. |

## Rules
- **Motion explains something.** Every technique answers: what changed, where did it go, what happens next? If it doesn't explain, delete it.
- **Transform + opacity only.** Never animate `width`, `height`, `top`, `left`, or `transition: all`.
- **One technique per moment.** A press is a scale OR a shade change, not both + a shadow. A reveal is a mask OR a fade, not both.
- **Reduced motion:** under `prefers-reduced-motion: reduce`, all of these become instant state changes. The state still changes — only the animation is removed.
- **Static first frame:** the design is complete without JS, media playback, or motion. Motion is additive, never required.
