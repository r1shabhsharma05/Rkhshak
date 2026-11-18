# Interaction Polish — the unseen details that compound

Distilled from Emil Kowalski's design-engineering philosophy (method in our own words). Use when building or reviewing a component's interactions and polish. Taste is trained, not innate: unseen details compound, and beauty is leverage — a component that responds correctly in every state feels expensive even before anyone can say why.

## Buttons must feel responsive
Add `transform: scale(0.97)` on `:active` (subtle: 0.95–0.98), with a ~160ms ease-out transition. This applies to any pressable element. Instant feedback is what makes a UI feel like it is listening.

## Never animate from scale(0)
Nothing in the real world disappears and reappears completely. Start entrances from `scale(0.9)` or higher, combined with opacity. Even a barely visible initial scale makes the entrance feel natural.

## Popovers are origin-aware
A popover scales in from its trigger, not from the centre: `transform-origin: var(--transform-origin)`. **Exception: modals.** Modals keep `transform-origin: center` — they are not anchored to a trigger.

## Tooltips: skip the delay on subsequent hovers
The first tooltip may wait; once the user is moving between labelled elements, later tooltips appear immediately. A delay on every hover punishes exploration.

## Transitions over keyframes for interruptible UI
Anything a user can fire twice in a second (toasts, toggles, menus) uses CSS transitions, which retarget from the current value. Keyframes restart from zero and feel broken under rapid input.

## Blur masks imperfect transitions
When a crossfade cannot be made clean (mismatched content, layout shift), a brief blur during the transition hides the seam. Use it to mask, never as decoration.

## Enter states with @starting-style
Use `@starting-style` for entry animations on mount, so elements do not flash in their final state first and do not need JS to set an initial state.

## Transform mastery
- `translateY` with percentages is relative to the element's own size — prefer it over hardcoded pixels.
- `scale()` scales children too; account for it when scaling containers with text.
- 3D transforms give depth cheaply (a slight rotateX on a card tilt); keep the angles small.
- Never drive a child's transform from a CSS variable on the parent — it recalculates styles for every child. Set `transform` on the element directly.

## clip-path for animation
`clip-path` is the sanctioned fourth animatable property (after transform and opacity). Uses: the inset shape for reveals, tabs with perfect colour transitions, hold-to-delete patterns, image reveals on scroll, comparison sliders. Animate `clip-path: inset(...)` rather than height.

## Gesture and drag details
- **Momentum-based dismissal:** a flicked element keeps its velocity into the exit; do not snap it back to a fixed duration.
- **Damping at boundaries:** when a drag passes its limit, resistance grows — the element follows the finger less and less, then springs back. Never a hard stop, never a free overshoot.
- **Velocity handoff:** when a gesture ends, the animation continues from the gesture's velocity, not from zero. The seam between drag and animation must be invisible.

## Review format (when reviewing a component)
For each finding: what it is, where it lives, what the user feels, the fix in one line. Flag by default; approval is earned. A component passes when every state (rest, hover, focus, active, disabled, loading, error) feels deliberate and every animation survives rapid, repeated input.
