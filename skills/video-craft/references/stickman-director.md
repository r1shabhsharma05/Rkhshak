# Stickman director — two modes, one approval gate

Distilled from `directing-stickman-videos` (MIT). Own words throughout.

## Two modes, one skill
- **Director mode** — creates an approved storyboard and standalone video
  prompts. The user approves the plan before anything is generated.
- **Autopilot mode** — produces narrated, captioned illustration-and-micro-
  animation videos through configured generation, following the same story
  and voice rules.

## Workflow
1. Read the storyboard template, style catalog, and voice-continuity rules
   before planning. Structure the narrative with the **5-stage
   high-completion engine**, timing scaled to the target duration:
   1. **Golden Hook** — instant curiosity via a counter-intuitive question
      or visual paradox, in the first seconds. Never open with platitudes.
   2. **Disrupting Assumptions** — state what everyone thinks is true, then
      shatter it in one sentence.
   3. **Unveiling Insider Secrets** — the hidden mechanics, the real obstacle.
   4. **Ultimate Truth Revelation** — the underlying business or human-
      psychology truth, maximum payoff.
   5. **Elevation & Discussion** — a memorable punchline plus a discussion
      prompt that sparks debate.
2. **Stop after the director's proposal and request explicit approval.**
   Produce Phase A in the user's language, with English voiceover and a
   reference translation.
3. If the user changes ratio, duration, style, theme, narration, scene
   structure, or global direction, **recompose Phase A and request approval
   again**. Topic approval, schedule pressure, or approval of an older draft
   is not approval of the current Phase A.
4. Only after approval of the current Phase A, produce Phase B (the per-clip
   generation prompts).

## Output rules
- Scale voiceover to roughly 20–25 words per 10-second clip. Give each clip
  three timed beats (e.g. 0–3s, 3–7s, 7–10s), at least four relevant visual
  devices, and a visual change every 2–3 seconds. Never leave the character idle.
- Drive motion with concrete character actions (leaping, touching glass,
  drawing luminous lines, opening doors), never abstract liquid/shape morphing.
- Keep character proportions, line weight, style, and narrator consistent
  across all clips. Freeze the character anchor in Phase A and repeat it
  verbatim in every clip — never replace it with "same character" or a fresh
  description. A moving arm replaces its previous pose rather than adding
  another arm. Style 1 stays monochrome with at most three saturated accent
  colours named in plain words; light theme is flat pure-white, no textures,
  gradients, or 3D depth.
- **Voice continuity (all styles):** choose one complete video-level voice
  profile in Phase A, then repeat its full frozen block verbatim in every
  clip. A scene, style, or character change must not recast the narrator.
  Lock timbre, register, accent, texture, delivery, pace, and recording
  treatment — not just "same narrator". Keep emotional progression in
  visuals/music, and mandate music continuity from clip 1.
- Narration is audio-only: no speech bubbles, dialogue boxes, captions, or
  visual transcription of the narration. Quote exact dialogue; forbid
  alteration, repetition, or visual transcription.
- No technical colour notation (hex, RGB, Pantone) inside generation prompts.
  Default generated clips to no visible words, letters, numbers, or interface
  copy; optional 2–5 word overlays go in a separate post-production note.
- Match every clip ending to the next clip opening through action, an
  important prop, screen direction, or a planned cut.
- Style-specific packs (e.g. dark-comedy prehistoric, cozy storytelling,
  historical cartoon) override the generic rules where they conflict — read
  the pack's reference before planning that style, and do not apply one
  style's character rules to another.

## Revision rules
Recompose rather than rename: 16:9 stages action across left/center/right
with lateral tracking and negative space; 9:16 uses depth, stacked motion,
vertical reveals, and interface-safe placement. A theme, ratio, duration, or
style change invalidates prior approval and needs a fresh visual-balance check.

## Final check
Apply the loaded reference's checklist. Repair every failed condition before
responding. Never invent unsupported facts, statistics, quotations, or product
claims.
