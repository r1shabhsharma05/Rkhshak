# Motion Audit — review, audit, and remove motion

Distilled from the review-animations, improve-animations, find-animation-opportunities, and remove-animations skills (method in our own words). Three jobs: review a diff, audit a codebase, remove excess motion. The reviewer defaults to flagging; approval is earned.

## Review a diff (the review bar)
Review motion code against this bar. Each item is an automatic block; a review that passes a diff with an open block has not been done.
- **Should it animate?** Run the frequency gate (`build-sequence.md` §1) and the purpose test (§2). An animation with no named purpose fails.
- **Easing.** `ease-in` on UI, or a built-in `ease-out` on a deliberate animation, fails. Curves come from tokens or the tables, never invented.
- **Duration.** UI over 300ms with no reason fails. Press feedback 100–160ms, tooltips 125–200ms, dropdowns 150–250ms, modals/drawers 200–500ms.
- **Physicality.** Entrances from `scale(0)` fail. Popovers anchored to the centre instead of their trigger fail (modals exempt).
- **Springs.** Bounce on a non-momentum interaction fails. A spring with no damping/response reasoning fails.
- **Interruptibility.** Keyframes on rapidly-triggered elements fail. An animation that restarts from zero on re-trigger fails.
- **Asymmetric timing.** A deliberate phase (hold-to-confirm) that is fast, or a system response that is slow, fails.
- **Performance.** A layout/paint property animated fails. A child's transform driven by a parent CSS variable fails. Motion-library props that run on the main thread under load fail (see `motion-performance.md`).
- **Transforms & clip-path.** `width`/`height`/`margin`/`padding`/`top`/`left` animated fails (accordion height excepted). `transition: all` fails.
- **Gestures & drag.** A gesture with no velocity handoff fails. A hard stop at a drag boundary fails (rubber-band instead). A gesture with no non-gesture alternative fails.
- **Masking imperfect crossfades.** A crossfade that visibly jumps fails — blur-mask it or rebuild it as a shared-element transition.
- **Stagger.** Everything entering at once fails where a 30–80ms stagger was earned; a stagger on a list the user must scan quickly (tables, search results, settings) fails.
- **Accessibility.** Missing `prefers-reduced-motion` fails. Ungated `:hover` motion fails. Content hidden if the script fails fails.
- **Cohesion.** Two easing families on one screen fail. Two systems animating the same property fail. Motion with no narrative role fails.
- **Debugging.** When feel cannot be settled from code, recommend the check: play it at 2–5× duration or in the animation inspector, step it frame by frame, test gestures on a real device, look again the next day with fresh eyes.

## Audit a codebase (read-only on source)
1. **Recon (always first).** Map what animates: search for animation APIs, transitions, keyframes, and motion-library usage. Note which files own the motion tokens.
2. **Audit (parallel).** For each animation, run the gate: frequency, purpose, speed, function. Score each one: keep, fix (with exact values), or remove.
3. **Vet, prioritise, confirm.** Confirm each finding against the running product. Rank by user impact, not by file count. Confirm the top items with the user before writing plans.
4. **Write plans.** Self-contained implementation plans for another agent to execute, one per item, with the exact values. The Auditor never applies its own plans.

### Required output format — opportunities
- **Part 1 — Opportunities table.** Each row: where, what should animate, purpose, tool, properties, curve, duration/spring, expected feel. Only items that passed the gate.
- **Part 2 — Rejected candidates (REQUIRED).** Every place considered and rejected, with the reason (frequency tier, no purpose, function hindered, speed impossible). A report without this part is incomplete — it proves the gate ran.
- **Part 3 — Verdict.** What to build, in priority order, and what the audit deliberately left alone.

## Remove excess motion
1. **The gate, in reverse.** For each existing animation, ask: frequency (does the user see this 100+ times a day?), purpose (can it be named?), speed (can it stay inside budget?), function (does motion help or hinder here?). An animation that fails any of the four is a removal candidate.
2. **Where to hunt.** Keyboard actions, high-frequency surfaces (lists, tables, navigation), functional data (numbers the user reads), decoration with no purpose (pulses, shimmers, breathing glows, parallax, hover scale on cards, every section fading in on scroll).
3. **Remove, then reduce.** Remove what fails outright. Reduce what is borderline (shorter duration, opacity-only, once instead of looped).
4. **Removal hazards.** Removing an animation can expose a teleport (content appearing with no bridge) — replace it with an instant state change plus a spatial cue, not with nothing. Removing a loading animation can expose a flash — keep the skeleton, drop the shimmer.
5. **Cleanup.** Delete the dead keyframes, the unused tokens, the orphaned classes, and the library import if nothing uses it any more. A removal that leaves dead code behind is half done.

### Required output format — removal
- **Part 1 — Removed and reduced.** Each item: where, what changed, why (which gate question it failed).
- **Part 2 — Kept (REQUIRED).** Every animation that stays, with the purpose that earns it. A removal without this part is incomplete — it proves the audit did not delete by default.
- **Part 3 — Cleanup and verdict.** What dead code was removed, and the final state: what moves, what does not, and why.
