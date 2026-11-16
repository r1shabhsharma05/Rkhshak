# Responsive Checklist — every breakpoint, touch, and safe area

Check the design at EVERY breakpoint, not just desktop. A screen that works at 1280px and breaks at 390px is not done.

## Breakpoints (check all four)
| Breakpoint | Width | What to check |
|---|---|---|
| Mobile | 360–430px | Single column, no horizontal scroll, thumb-reachable primary action, text readable without zoom. |
| Tablet | 768–834px | Two-column where it helps, nav collapses or adapts, cards don't stretch into dead bands. |
| Desktop | 1280–1440px | The composed layout, max container width, gutters grow (measure doesn't). |
| Ultrawide | 1920px+ | Container capped and centred; gutters grow, measure and grids do not. No stretched hero, no dead band. |

At each breakpoint: no horizontal scroll, no clipped text, no overlapping elements, no dead band (empty space with no material and no job), images crop correctly (aspect ratios + `object-fit`), tables either scroll horizontally inside their container or reflow.

## Touch
- Minimum touch target **44×44px** for every interactive element (buttons, links, inputs, toggles, tabs). No exceptions.
- Touch targets have at least **8px** of space between them.
- Hover-only interactions must have a touch equivalent (no hover-only menus, tooltips, or reveals).
- No `hover:scale` on cards (motion tell). Tap states are visible and immediate.

## Safe areas
- Content respects the notch, Dynamic Island, home indicator, and status bar: use `env(safe-area-inset-*)` (or the platform equivalent), never hardcode the inset.
- Nothing essential sits under the notch or home indicator. Bottom actions clear the home indicator.
- Full-bleed images/fields may bleed, but text and controls never do.

## Text at small sizes
- Body text **16px or larger** at mobile (prevents iOS auto-zoom on inputs — inputs are 16px+ too).
- For a video or thumbnail, and only then, keep 24–32px of air, let nothing hit the frame edge unless it's meant to bleed, and keep every word people need at 16px or larger at that size.
- Line length: 45–75 characters per line on desktop, shorter on mobile. Long lines get a narrower measure, not smaller type.

## Orientation + zoom
- Works in portrait and landscape (no broken layout on rotate).
- Works at 200% browser zoom (text reflows, nothing clips, no horizontal scroll from zoom alone).
