# Physical Motion — springs, gestures, and the feel of real objects

Distilled from Apple's approach to interface design and fluid, physical motion (apple-design-emil) and Emil Kowalski's spring guidance. Method in our own words; spring values are the sources' published values. Use when the motion is touched: drag, swipe, sheets, momentum, or anything a user can interrupt.

## The core idea
Think of animation as a conversation between you and the object, not something prescribed by the interface. A pre-scripted, fixed-duration animation cannot respond to new input. A spring can — new input just changes the target, and the motion stays continuous. Reach for springs for anything a user can touch.

## 1. Response — kill latency
The interface must acknowledge input immediately. A press that waits for an animation to start feels dead, however beautiful the animation is. Feedback first, choreography second.

## 2. Direct manipulation — 1:1 tracking
When the user drags something, it follows the finger exactly, with no lag and no easing applied on top. Any smoothing is applied after release, never during the drag.

## 3. Interruptibility — the single most important principle
Every animation must be interruptible at any point and retarget cleanly from its current value. Springs do this naturally; fixed-duration animations do not. If a user reverses mid-animation, the object reverses from where it is, not from where it started.

## 4. Springs, not durations
Think in two designer-friendly parameters, not the physics triplet:
- **Damping ratio** — controls overshoot. `1.0` = critically damped, no bounce, smooth settle. Below `1.0` = overshoots and oscillates. Lower = bouncier.
- **Response** — how quickly the value reaches the target, in seconds. Lower = snappier. This is not "duration" — a spring has no fixed duration; its settle time emerges from the parameters.

**Defaults:** start most UI at damping `1.0` (critically damped). Add bounce (damping ~`0.8`) **only when the gesture itself carried momentum** (a flick, a throw, a drag release). Overshoot on a menu that just faded in feels wrong; overshoot on a card you flicked feels right.

**Concrete values:**
| Interaction | Damping | Response |
|---|---|---|
| Move / reposition | `1.0` | `0.4` |
| Rotation | `0.8` | `0.4` |
| Drawer / sheet | `0.8` | `0.3` |

**Web mapping:** in Motion/Framer Motion, `bounce: 0` springs everywhere by default (its `damping` is a physics coefficient, not Apple's damping ratio); reserve bounce for momentum-driven, physical interactions. A safe house style is `{ type: "spring", duration: 0.5, bounce: 0.2 }` for Apple-style motion, keeping bounce at 0.1–0.3 and avoiding it in most UI.

**When to use springs:** drag with momentum, an element that should feel alive, a gesture the user can interrupt or reverse, decorative mouse-tracking. **When not to:** anything on the frequency gate's high tier, and any state change where a fixed short duration is clearer.

## 5. Velocity handoff
When a gesture ends, the animation continues from the gesture's velocity, not from zero. The seam between drag and animation must be invisible: measure the release velocity and feed it into the spring's initial velocity.

## 6. Momentum projection
Animate to where the gesture is *going*, not where it stopped. Project the release velocity forward to pick the target (e.g. dismiss vs snap back), then animate to that target. A flick that would carry an element past its threshold dismisses it; one that would not snaps it back.

## 7. Spatial consistency
Symmetric paths: exit the way it entered. Anchored origins: a popover grows from its trigger. The object keeps its identity through the motion — it moves, it does not teleport and it does not become a different thing.

## 8. Hint in the direction of the gesture
Before the user commits, show where the gesture leads: a sheet that lifts slightly when pulled, a card that tilts toward the swipe. The hint is small, reversible, and costs nothing if the user lets go.

## 9. Rubber-banding — soft boundaries
When a drag passes its limit, resistance grows — the element follows the finger less and less, then springs back. Never a hard stop, never a free overshoot.

## 10. Gesture design details (feel checklist)
- Momentum-based dismissal: a flicked element keeps its velocity into the exit.
- Damping at boundaries (see §9).
- The gesture works on the first try, without a tutorial, and has a visible non-gesture alternative (a button, a menu item).
- Multimodal feedback: motion + sound + haptics together, each quiet on its own. Haptics confirm; they never nag.

## 11. Frame-level smoothness
60fps is the floor (16.7ms per frame; 8ms at 120Hz). Springs run on the compositor thread where the platform allows it; see `motion-performance.md`. A spring that drops frames feels worse than no spring at all.

## 12. Materials and depth
Translucency conveys hierarchy: the floating layer is translucent, the content layer is not. Depth comes from layers and motion, not from shadows and glows.

## 13. Reduced motion and accessibility
Under reduced motion, springs become instant state changes or gentle opacity fades — the content and the outcome stay identical. Every gesture has a non-gesture path.

## 14. Typography (motion-adjacent, for completeness)
Optical sizing, tracking, and leading change with size: display type tracks tighter (−0.02 to −0.05em) with leading 0.85–1.05; text tracks near zero with leading 1.45–1.6. Motion never compensates for type set at the wrong size.
