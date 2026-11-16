# Micro-interactions — feedback for every touch

A micro-interaction is the product answering a touch. It is not decoration. Every interactive element answers immediately (within 100ms) so the user knows their touch landed.

## Patterns (one per interaction, consistent everywhere)
| Interaction | Feedback | Duration |
|---|---|---|
| Button press | Scale to 0.97 + a subtle shade change. Never `hover:scale` on cards. | 100–150ms |
| Toggle / switch | Thumb slides + track color changes. The state is readable without color (position + label). | 150–200ms |
| Checkbox / radio | Checkmark draws in (or fades in). Never a bounce. | 150ms |
| Drag | The dragged item lifts (one depth cue — a soft shadow) and the drop target highlights. Ghost the original position. | Follows the finger (no easing on drag) |
| Swipe | The item follows the finger, then snaps to its end state (dismissed / revealed actions). Show the action that will happen (delete/archive) as the item moves. | Snap: 200ms ease-out |
| Pull to refresh | The indicator appears, then the content updates. Never a full-screen spinner for a refresh. | Follows the pull |
| Long press | Haptic (where available) + a contextual menu or a selection state. The user must know a long press exists (a hint, not a secret). | Immediate |
| Copy | "Copied" confirmation near the button (not a toast in the corner). The button briefly changes to a check. | 150ms + 1.5s confirmation |
| Like / favorite | The icon fills + a small scale pop (1.0 → 1.2 → 1.0). One pop, not a burst of particles. | 200ms |
| Loading (button) | The button shows progress (spinner inside the button, label stays) and can't be double-tapped. The form can't double-submit. | Until done |

## Rules
- **Immediate.** Feedback starts within 100ms of the touch. A delay feels broken.
- **One cue.** A press is a scale OR a shade change, not both + a shadow + a sound. One depth cue per surface.
- **Consistent.** The same interaction behaves the same way everywhere. A toggle on settings works like a toggle on the profile.
- **Reversible.** Every destructive micro-interaction (swipe to delete, long-press to remove) has an undo, shown where the action happened.
- **Reduced motion:** under `prefers-reduced-motion`, micro-interactions become instant state changes (no scale, no slide). The state still changes — only the animation is removed.
- **No feedback is a bug.** A button that does nothing when tapped (no press state, no loading, no result) is broken, even if the action eventually completes.
