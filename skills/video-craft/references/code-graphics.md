# Code-drawn graphics — Manim, isometric SVG method, fetching media

Distilled from `manim` (MIT, Manim Community v0.22.0), `anatomy` (MIT/CC-BY
— method distilled only, no assets, no blobs, no large files), and
`ghost-downloader` (GPLv3, xiaoyouchr/ghost-downloader-3 — usage playbook
only, no code copied). Own words throughout.

## Manim — code-to-video animation
- Scenes are Python classes subclassing `Scene` with a `construct(self)`
  method. Primitives: text, shapes, axes + plots; animations: Create,
  Transform, FadeIn/FadeOut, Write, waits. LaTeX-rendered maths (`Tex` /
  `MathTex`) works where a TeX install exists — verify before promising it.
- **Workflow:** write the scene file under a work dir (never in a client repo
  unless asked). Draft at low quality (480p), check timing/composition from
  the MP4, iterate, final at high quality (1080p) only after the draft reads
  right. Keep scenes short and single-idea (~5–15s per concept); dark
  background by default, one accent colour per idea.
- **Deliver the actual .mp4 file.** A render path alone is not a deliverable.
- Use when a video/animation explains better than text: concept breakdowns,
  data stories, algorithm visualisations, educational posts.

## Isometric SVG explainer method (no assets — the method only)
Build crafted, highly detailed, interactive isometric SVG figures that explain
a technical idea as a real physical object (a test rig, a dial gauge, a
cabinet of drawers, a plotter, a lock), with many small precise solid parts,
four-tone shading, correct painter's order, and readable labels. This skill
carries the method, not the source kit's 40MB of assets.
- **Solids, not wireframes.** Every part is filled and painted in order, so
  things in front hide things behind. No see-through edges, no dashed hidden
  lines.
- **Tone hierarchy.** Base/feet darkest, structure mid, subject brightest.
  Exactly one accent is the brightest: the part the reader should watch.
  Use colour only when colour is the subject.
- **Small precise detail, never noise.** Bevels, grooves inset from edges,
  screws as dots with rings at plate corners, knurls on knobs, ruler ticks,
  a label plate with rule lines. Each detail belongs to a part.
- **Lines resolve.** Every line ends on something: a face, another line, or a
  terminal dot. No leader lines, balloons, dimension arrows, or labels
  floating in the air.
- **No pipe or cable passes through anything** — not through another pipe,
  cable, or solid, in any frame. Keep clearance; run lines beside the
  structure, never across the subject's face.
- **Every crossing is drawn in true depth order.** Where two items overlap,
  the nearer is drawn on top — proved by the draw order, not tuned by eye.
- **Curved surfaces shade smoothly, never in a staircase.** Seams go under
  the outline; tone bands taper to nothing instead of ending on a straight cut.
- **A texture ends on a real edge or fades.** Ribs, bolt circles, seams, and
  grooves never stop in the middle of a surface.
- **Composition.** Centre the figure; let it fill about 55–65% of the card.
  Keep a consistent scale across a set; make sure it still reads at phone width.
- **Shaders (WebGL) only for what lines cannot draw** — fire, water, real lamp
  light, glow, steam. Parts stay SVG. Every effect rides an envelope with
  attack and decay; nothing pops, nothing cuts off hard at an edge.

## Fetching source media (local download manager)
- A local download manager (CLI + desktop app, aria2-compatible RPC) fetches
  HTTP, magnet/BT, FTP, M3U8, DASH, video-platform, and mirror links — one
  persistent install, never re-cloned.
- The CLI is a **client of the running app instance**: with no live instance
  it auto-spawns one; if that spawn dies the CLI reports the instance as
  unavailable. The CLI never works without a live app process, and the app
  does not survive a machine restart — relaunch it after one before using the
  CLI.
- Surface: probe a URL, add URLs, list tasks, inspect/pause/start/remove/wait
  on a task by id.
- Download only media the user has a right to use, and say where each file
  came from. The app's own update check may fail on a proxied host — that is
  non-blocking; task operations still work.
