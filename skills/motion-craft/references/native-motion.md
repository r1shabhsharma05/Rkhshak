# Native Motion — Expo / React Native

Distilled from the animate-expo skill (method in our own words; library names and API shapes are cited, not copied). Use when animating anything in an Expo / React Native app. For web animation use the main build sequence; the gate and the purpose are the same, the tools and the thread are not.

## The build sequence (same gate, native tools)
1. **Should this animate at all?** The frequency gate applies unchanged — 100+ times/day means no animation, ever. Keyboard-initiated actions are a disqualifier.
2. **What is the purpose?** Name it (feedback, spatial consistency, state indication, preventing a jarring change, explanation, delight at the rare tier only).
3. **Pick the tool — cheapest that works.** CSS-equivalent transitions first; Reanimated for springs, layout animations, exit animations, and gesture-driven values; Gesture Handler for drag/swipe; Expo Router for screen transitions; expo-haptics for confirmation.
4. **Pick the properties.** Transform and opacity only — same rule as web, same exceptions.
5. **Timing or spring.** Springs for anything touched or interruptible (see `physical-motion.md`); fixed durations for the rest, from the same duration table (press 100–160ms, small popovers 125–200ms, modals/sheets 200–500ms).
6. **Keep it off the JS thread.** Animation work runs on the UI thread (Reanimated worklets). Anything that runs on the JS thread drops frames while the app is busy — never animate through React state per frame.
7. **Press, not hover.** There is no hover on touch. Feedback is press (scale 0.97), haptics, or both. Never gate feedback on a hover that cannot happen.
8. **Haptics.** A light haptic confirms an action; it never nags. Haptics accompany motion, they do not replace it. Respect the system haptic setting.
9. **Reduced motion and accessibility.** Reduced motion means fewer and gentler animations, not zero — content and outcome stay identical. Every gesture has a visible non-gesture alternative.

## Setup that silently breaks motion
- A Reanimated version mismatch with the Expo SDK (check the SDK's compatible version first).
- The Babel/Reanimated plugin missing or misordered — animations silently fall back to the JS thread.
- Gesture Handler's root view missing — gestures silently do nothing.
- A screen transition configured in two places (router + a manual animation) fighting over the same property.
Check these four before debugging any value.

## 120fps
Where the device supports it (most current phones), the frame budget is 8ms, not 16.7ms. Design against 8ms: composite-only properties, no per-frame JS-thread work, no layout animation on large lists.

## Recipes
Start from a recipe, not a blank file, for the common cases: button press, sheet, toast, tab indicator, drag-to-dismiss, pull-to-refresh, shared-element transition, stagger. A recipe is a starting point — adapt its values to the codebase's tokens.

## Never Ship (native additions to the web list)
| Never | Instead |
|---|---|
| Animation through React state per frame | Reanimated shared values / worklets |
| Hover-gated feedback | Press + haptics |
| A gesture with no root handler view | Wire the handler root first |
| Haptics on every interaction | Haptics on confirmation only |
| 120fps assumed | Design against 8ms, verify on device |

## Output
Write the code. Then, in at most a few lines: the gate result (frequency tier + named purpose), the ingredients (tool, properties, curve/duration or spring, thread), and what to feel-check on a real device.
