# Handoff — Figma / dev handoff specs

A design is not done until a developer can build it without guessing. The handoff is the spec: measurements, assets, states, and behavior — everything the builder needs, nothing they have to ask for.

## What the handoff contains
1. **The screens** (final, at every breakpoint — mobile, tablet, desktop). Each screen is labeled with its route/name.
2. **The system** (`design.md` — the locked tokens, type scale, components, and rules). The developer reads this first.
3. **Measurements:** spacing (4px grid), sizes, and gaps — as tokens, not one-off pixels. Every measurement comes from the token scale.
4. **Assets:** every image/icon/logo, exported at the right sizes (1×, 2×, 3× for mobile; SVG for icons/logos), named clearly, with alt text.
5. **States:** every component in all its states (default, hover, focus, active, disabled, error, loading, empty, success). A component with one state in the handoff is an unfinished component.
6. **Behavior:** what happens on tap/click/scroll (micro-interactions, motion durations + easing, what the moment does, what the next state is).
7. **Content:** real copy (not lorem ipsum), real data examples, and the empty/error copy for each state.
8. **Edge cases:** long names, long numbers, no data, error, offline — what the screen looks like then.

## Format
- **If the team uses Figma:** the file is organized (pages per flow, frames named by route, components as real Figma components with variants for states, styles as Figma styles linked to tokens, auto-layout everywhere). No detached instances, no unnamed layers ("Frame 47", "Rectangle 12").
- **If there is no Figma file:** the handoff is a written spec (this file's checklist) + the built screens (screenshots at every breakpoint) + the `design.md` + the tokens file. The developer builds from the spec, not from a screenshot alone.
- **Redlines:** annotate the key measurements on the screens (spacing, sizes, type) — but the tokens are the source of truth, not the redlines.

## Rules
- **No lorem ipsum.** Real copy or clearly-marked placeholder copy ("[Client name]", "[Invoice total]") that the developer knows to replace.
- **No "make it look like the screenshot".** The spec (tokens + states + behavior) is what gets built. A screenshot is a reference, not a spec.
- **One source of truth.** If the Figma file and `design.md` disagree, `design.md` wins (or the Figma file is updated in the same change).
- **The developer can ask.** The handoff names who to ask (the designer) and what is still open (slots, missing assets, undecided copy).
