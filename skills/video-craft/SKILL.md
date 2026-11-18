---
name: video-craft
description: "Direct and produce short videos — stickman explainers, premium talking-head reels, HTML-to-video, code-to-video, full-pipeline productions — analyse a video, generate voiceover, and keep audio in sync. Use when the user wants a video made, a reel built, a video analysed, or narration generated. Approves the plan before building; verifies the file before delivery; never posts without the user's explicit yes."
---

# Video Craft — approve the plan, build it, verify the file

## Purpose
Video work fails in expensive ways: a render that plays fast because the
audio was never resampled, a storyboard built on an approval the user never
gave for the current version, a file claimed done that nobody watched. This
skill directs a video from brief to verified file — story first, approval
second, build third, verification last — across stickman animation,
talking-head reels, HTML-to-video, code-to-video, and full-pipeline production.

Use it when the user wants a video made (explainer, reel, documentary
montage, talking-head, animation), a video analysed or answered from, a
voiceover or dub, or an audio mix assembled. For still images and design of a
screen, use design-unslop; for motion on a UI, use motion-craft.

## Hard rules (never broken)
- **Approval gates are real.** A storyboard/plan is approved before prompts
  or renders are produced. Approval of an older draft is not approval of the
  current one — any change to theme, ratio, duration, style, narration, or
  scene structure recomposes the plan and needs fresh approval.
- **Verify the file before claiming done.** ffprobe + a real frame watch
  (caption sync, audio sync, safe areas) on the actual MP4. A render path
  alone is not a deliverable; the MP4 file itself is.
- **Never post or publish without the user's explicit yes.** Schedule is not
  post. Nothing auto-posts, auto-uploads, or goes live from this skill.
- **No invented facts.** No unsupported statistics, quotations, or product
  claims in scripts, narration, or captions.
- **Voice only with permission.** Clone or use a person's voice only when the
  user authorised that voice. A generic narrator voice is the default.
- **Deterministic renders.** No `Date.now()`, no unseeded randomness, no
  render-time network fetches.
- **Keys are the user's step.** Paid providers need the user's key AND explicit
  yes, with a cost estimate before generation starts. Never put a key in chat,
  memory, or a file outside the provider's own config.

## Workflow
1. **Pick the tool by the brief** (cheapest that expresses the design):
   - Stickman explainer / faceless story → `references/stickman-director.md`
   - Generated-media video with directed components → `references/hypit.md`
   - Premium talking-head reel (kinetic captions) → `references/lapoz-reels.md`
   - Motion-graphics-led build, HTML/CSS/GSAP → `references/hyperframes.md`
   - Full pipeline (research → script → assets → compose) → `references/openmontage.md`
   - Math/concept explainer, code-drawn → `references/code-graphics.md` (Manim + isometric SVG method)
   - Watch/answer a video, or voiceover/dub → `references/watch-voice-audio.md`
2. **Plan from the material.** Transcribe first where speech drives the cut;
   plan from the transcript. Cut pauses, fillers, dead sections. Keep
   talking-head reels near 10 seconds unless the brief says otherwise.
3. **Director proposal → approval.** Phase A (storyboard, style, voice, ratio,
   duration) is shown and approved before any generation. One signature
   element per template/style, kept consistent throughout.
4. **Build.** Follow the chosen reference's work loop and its own gates
   (lint + check before render, draft quality before final, and so on).
5. **Audio gate.** Probe every voice segment, resample all to one mix rate,
   verify the assembled mix. See `references/watch-voice-audio.md`.
6. **Verify and deliver.** ffprobe, frame watch, caption/audio sync, safe
   areas. Deliver the MP4 file. Report what was verified, not what was
   assumed.

## References
| File | What it covers |
|---|---|
| `references/stickman-director.md` | Stickman videos — director vs autopilot, 5-stage story engine, style catalog, voice continuity |
| `references/hypit.md` | Hypit — directed generated-media video, component authoring, voice continuity |
| `references/lapoz-reels.md` | Premium talking-head reels — four templates, word-level karaoke captions, render + verify |
| `references/hyperframes.md` | HTML-to-video — composition contract, registry-first, lint + check gates, deterministic render |
| `references/openmontage.md` | Full-pipeline production — pipeline-first, capability envelope, zero-key path, runtime choice |
| `references/watch-voice-audio.md` | Watch a video + voiceover — engines, transcript limits, voice generation, sample-rate gate |
| `references/code-graphics.md` | Code-drawn graphics — Manim scenes, isometric SVG explainer method, fetching source media |

## Provenance
Distilled in our own words from: `directing-stickman-videos` (MIT); `hypit` (MIT); `lapoz-reels` (original implementation of an observed method — holds none of the vendor's paid files, never claims an output was made by the vendor); `hyperframes` (Apache 2.0, heygen-com/hyperframes); `openmontage` (AGPLv3, calesthio/OpenMontage — method distilled only, no code copied; the tool itself is AGPL, so hosted/modified use triggers its source-sharing terms); `watch` v0.3.2 (MIT); `voicestudio` (MIT, debpalash/VoiceStudio); `video_audio_sample_rate_gate`; `manim` (MIT, Manim Community v0.22.0); `anatomy` (MIT/CC-BY — method distilled only, no assets, no blobs); `ghost-downloader` (GPLv3, xiaoyouchr/ghost-downloader-3 — usage playbook only, no code copied). No source text copied verbatim beyond short terms of art; no project names, personal data, or credentials carried over.

## Report format
Tool picked (and why) · plan approved (what version) · build (what was rendered, at what quality) · audio gate (rates probed/resampled) · verification (ffprobe + frame watch results) · delivered file (path) · what still needs the user's yes (post/publish, paid generation).
