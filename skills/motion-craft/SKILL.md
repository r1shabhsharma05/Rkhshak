---
name: motion-craft
description: "Build, review, audit, or remove UI motion so it feels right — decide whether something should animate at all, name its purpose, pick the cheapest tool, the right properties, curve and duration, and handle interruption, exit, and reduced motion. Use when asked to animate something, add motion, make a component feel alive, fix janky animation, audit a codebase's motion, find what should (or should not) animate, remove excess animation, or name a motion effect. Covers web and native (Expo/React Native) motion, springs and physical motion, frame-budget performance, and the motion vocabulary. Design-unslop owns the whole screen; motion-craft owns the movement on it."
---

# Motion Craft — make movement feel right

## Purpose
Motion is a discipline, not a garnish. Most bad motion is not badly executed — it is motion that should not exist, or motion built with the wrong ingredients (`ease-in` on an entrance, `scale(0)`, keyframes on a toast, a 400ms dropdown). This skill turns a request for motion into an implementation that survives a strict review, audits motion that already exists, and removes motion that earns nothing. The bar is Emil Kowalski's animation philosophy, Apple's physical-motion principles, and the frame budget.

Use it when the user asks to animate something, add motion, make a component feel alive, build a transition, fix janky or slow animation, audit or improve a codebase's motion, find what could animate, tone motion down, or name an effect ("what's it called when…"). For the whole screen — direction, layout, type, colour — use design-unslop; for the movement on it, use this skill.

## When NOT to use
- For a quick prototype the user explicitly wants rough/fast (say so, do not run the full gate).
- To add motion to a screen the user did not ask to change. Motion is never a redesign.
- As a substitute for fixing the underlying interaction. Motion that decorates a confusing flow is still a confusing flow.

## Multi-agent roles (never one agent doing all three)
| Role | Job | Must NOT do |
|---|---|---|
| **Builder** | Run the build sequence, write the implementation. | Review its own motion. Declare it "done". |
| **Reviewer** | Fresh eyes: run the review bar in `references/motion-audit.md` independently, with the running product, not the Builder's word. | Change the motion. Trust the Builder's word without evidence. |
| **Auditor** | Survey a codebase's motion and write prioritised plans (read-only on source). | Apply the plans. Score its own plans. |

One agent per role. If only one agent is available, it builds only and reports — it does not review and approve its own work.

## Workflow — build
1. **Gate first.** Run `references/build-sequence.md` step 1 (frequency) and step 2 (purpose). If the request fails the gate, say so plainly and write no animation. Offer the non-motion alternative instead. Zero lines of code is a success here, not a dodge.
2. **Pick the tool.** Cheapest that works: CSS transition → CSS `@starting-style` → CSS animation → WAAPI → a motion library. Never install a motion library for a fade. If the task needs a component (toast, drawer, command menu, dropdown), stop and pick one from a component library — hand-rolling those is how a `<div>` dropdown with no focus management is born.
3. **Pick the properties, curve, duration.** Transform and opacity only (clip-path is the sanctioned fourth; height is tolerated only for accordions). Never `scale(0)` — start from `scale(0.9–0.97)` + `opacity: 0`. Easing and duration from the tables in `references/build-sequence.md`, or from the codebase's existing tokens — never invent a curve because it looks familiar. Extend the codebase's tokens; do not fork them.
4. **Interruption and exit.** Transitions, not keyframes, for anything triggered rapidly. Springs for gestures. Exit the way it entered. Asymmetric timing where the user is deciding (slow on the deliberate phase, snappy on the system response).
5. **Reduced motion and pointer gating ship with the animation**, not as a follow-up. Reduced motion means fewer and gentler animations, not zero. Hover motion is gated to `(hover: hover) and (pointer: fine)`.
6. **Physical motion (when the motion is touched).** If the motion is drag, swipe, sheet, or momentum-driven, use `references/physical-motion.md`: springs over fixed durations, velocity handoff, rubber-banding, interruptibility.
7. **Performance check.** Run `references/motion-performance.md`: composite-only properties, the 16.7ms frame budget (8ms at 120Hz), off the main thread where it matters. If it drops frames, diagnose before tuning values.
8. **Review.** The Reviewer runs the Never Ship list in `references/build-sequence.md` plus the review bar in `references/motion-audit.md`. Each item is an automatic block. Approval is earned.

## Workflow — audit / improve / remove
1. **Recon.** Map what animates: search the codebase for animation APIs, transitions, keyframes, and motion-library usage. Read-only on source.
2. **Audit.** For each animation, run the gate (frequency, purpose, speed, function) from `references/motion-audit.md`. Produce two lists: opportunities (with exact values) and rejected candidates (with the reason each was rejected — the rejected list is required, not optional).
3. **Vet and prioritise.** Confirm each finding against the running product. Rank by user impact, not by file count.
4. **Write plans.** Self-contained implementation plans for another agent to execute, one per item, with the exact values. The Auditor never applies its own plans.
5. **Remove.** For excess motion, use the removal workflow in `references/motion-audit.md`: remove, reduce, clean up what the removal leaves behind, and list what was kept and why.

## Workflow — name an effect
Use `references/motion-vocabulary.md` to reverse-look-up the term for a described effect ("the bouncy thing when a popover opens" → Pop in). Name the effect, then stop — naming is not designing or building.

## Workflow — native (Expo / React Native)
Use `references/native-motion.md`: the same gate and purpose, then the native tool ladder (Reanimated, Gesture Handler, Expo Router, haptics), kept off the JS thread, press-not-hover, 120fps where the device supports it.

## References
| File | What it covers |
|---|---|
| `references/build-sequence.md` | The build sequence — the frequency gate, purpose, tool ladder, properties, easing/duration tables, interruption and exit, reduced motion, the Never Ship list |
| `references/physical-motion.md` | Physical motion — springs (damping ratio + response), direct manipulation, interruptibility, velocity handoff, momentum, rubber-banding, materials and depth |
| `references/motion-performance.md` | Frame-budget performance — what to animate, where it runs, the symptom table, will-change, React pitfalls, diagnosis workflow |
| `references/motion-vocabulary.md` | Reverse-lookup glossary — the exact term for a described effect, by family |
| `references/motion-audit.md` | Audit, review, and removal — recon, the review bar, opportunities + rejected candidates, prioritised plans, removal hazards and cleanup |
| `references/native-motion.md` | Native motion — Expo/React Native build sequence, threads, gestures, haptics, 120fps, setup that silently breaks motion |

## Rules
- **The gate comes first.** Steps 1 and 2 of the build sequence decide everything. Never reach for a curve before knowing whether it animates at all.
- **No approximated values.** Every curve, duration, and spring config comes from the codebase's existing tokens or the tables in this skill. Never invent one because it looks familiar.
- **Cheapest tool that works.** Do not install a library for a fade.
- **Never present motion options as a menu.** Make the call, state the reasoning in one line, write the code.
- **Reduced motion ships with the animation.** Every time, no exceptions.
- **Feel that cannot be settled from code is said, not guessed.** If a spring's bounce or a crossfade depends on feel, point at the check: play it at 2–5× duration or in the animation inspector, step it frame by frame, test gestures on a real device, look again the next day with fresh eyes.

## Report format
Gate result (frequency tier + named purpose, and what was rejected and why) · ingredients (tool, properties, curve, duration or spring config, one line each) · what to feel-check (if any) · review verdict (blocks found: none / list).
