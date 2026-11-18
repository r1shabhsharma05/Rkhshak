# Lapoz-style premium reels — one clip in, motion graphics out

Distilled from `lapoz-reels` — an original implementation of a method
observed from the vendor's public page and the surrounding code-to-video
ecosystem. It holds none of the vendor's paid files. **Never claim an output
was made by the vendor, and never copy the vendor's paid files.**

## When to use it
- The user asks for a premium talking-head reel, kinetic captions, or names
  the Layercut, Spiral, Eclipse, or Aurora templates.
- The design is motion-graphics-led and a plain captioned clip would look
  flat. For a plain captioned reel, the simpler ffmpeg pipeline stays the
  default.

## Pipeline
1. **Take one raw talking-head clip as the only input.** Ask for the clip and
   the template pick before starting. No clip, no build.
2. **Transcribe with word-level timestamps** (faster-whisper or equivalent).
   Plan from the transcript before writing any code. Cut pauses, fillers,
   and dead sections. Pick the key words that earn a pop. Keep talking-head
   reels near 10 seconds.
3. **Write one HTML composition per video.** Default 1080×1920 vertical for
   reels (1080×1080 square only when asked), 60fps. Put the speaker video in
   with `class="clip"`. Drive all motion from one paused GSAP root timeline
   on `window.__timelines`.
4. **Check the component registry before hand-building any named visual.**
   Use the registry's transitions, overlays, titles, kinetic type, captions,
   charts, maps, and camera moves where they exist.
5. **Render with the HTML-to-video renderer** (see `hyperframes.md`). Run
   `lint` and `check` and pass both before rendering. Keep the render
   deterministic: no `Date.now()`, no unseeded `Math.random()`, no render-time
   network fetches.
6. **Verify the MP4** with ffprobe plus a real frame watch before claiming it
   is done. Check caption sync, audio sync, and that no text sits under
   platform UI zones.
7. **Deliver the MP4 file itself.** Never post or publish without the user's
   explicit yes. Schedule is not post.

## The four templates (one signature element each — never two)
- **Layercut** — the motion-graphics edit. One key word behind the head with
  subject layering. Auto-cut pauses and fillers. A 3D page fly-over for
  section changes. For explainers and long-form cuts.
- **Spiral** — premium 10-second talking-head reel. A glass ribbon behind the
  speaker, cards behind the head, tiles popping on key words as spoken. Use
  it when the reel must feel expensive in the first second.
- **Eclipse** — premium 10-second talking-head reel. A glowing ring behind
  the head, chips popping on spoken words, a portal scene on the key word.
  Use it when one idea must land hard.
- **Aurora** — the explainer edit. Speaker in a rounded panel, gold karaoke
  captions, pull quotes, compare/list cards for the argument. For teaching
  and breakdowns.

## Caption rules
- Time captions **word by word** from the transcript timestamps, never line
  by line. Highlight the current word and pop the key words.
- Keep captions inside the safe area — top and bottom clear of platform UI.
  One font family for the whole video. Gold is the Aurora caption colour;
  white with a dark outline is the default elsewhere.
