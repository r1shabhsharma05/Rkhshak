# Watch a video + voiceover — evidence limits, voice generation, audio gate

Distilled from `watch` v0.3.2 (MIT), `voicestudio` (MIT,
debpalash/VoiceStudio), and `video_audio_sample_rate_gate`. Own words;
local install paths are not carried over.

## Watch a video (answer from evidence, not from guessing)
- Two engines: a **video model** (needs the user's API key; the video is sent
  to the provider and deleted after the answer) or a **local engine** (frames
  + transcript extracted on the machine, no key needed). Ask which engine once
  per session; do not re-ask every video.
- **Native captions come first.** The transcript comes from captions; a local
  or cloud transcriber is only a fallback. Detail levels run lightest to
  heaviest: transcript only → fast keyframes → scene-aware frames.
- **Transcript-only evidence cannot establish visual facts.** If only a
  transcript is available, answer what was said and refuse/defer what was
  shown (colours, on-screen text, actions) — and name what would settle it
  (frames, or the video model watching the video). Never guess a visual fact.
- Setup: run the setup check first; if it reports it cannot proceed, confirm
  the missing binaries become available before watching. Keys are never
  printed or put in a shell command.
- Downloading uses yt-dlp, frames use ffmpeg, transcripts use captions first.
  Report timestamps with every claim that has one.

## Generate speech (VoiceStudio)
- Use the user's running VoiceStudio backend (local by default). Check
  health first, then discover the running version's contracts (OpenAPI schema,
  voices/engines) — do not invent profile IDs or infer installed models from
  a catalog listing. If the backend is unavailable, launch the installed app;
  do not install a second backend or overwrite an existing checkout.
- Prefer a discovered saved voice for repeatable narration. Model/voice
  aliases are compatibility names, not quality guarantees and not other
  providers' actual voices. Check the installed engine's language and
  voice-design capabilities before promising a result.
- Check the HTTP status and decode/probe the output before calling it audio:
  an error response can be written to the output path. Report the saved path
  and actual duration/format. Never fabricate a successful generation,
  transcript, or job completion.
- **Clone only voices the user is authorised to use.** Preserve reference
  files and existing profiles. For dubbing, retain the original media,
  speaker assignments, segment timing, and background-audio intent —
  translation completion is not rendered-dub completion. For async work, use
  returned job IDs and documented progress/status endpoints; inspect terminal
  errors instead of blindly resubmitting a timed-out generation.
- Transcribe with the backend's transcription endpoint (plain text, or
  timestamped/ subtitle formats when supported). Check transcription-model
  readiness before long recordings; a missing model needs download
  authorisation, never a silent install.
- Local configurations may permit unauthenticated calls; protected deployments
  need the configured credentials. Treat 401/403 as authentication failures,
  not permission to disable auth. Never print tokens.

## The audio sample-rate gate (run on every mix)
1. **Probe every voice segment before assembly.** Run ffprobe on each segment
   and record its sample rate, channel count, and duration. Flag every
   mismatch against the planned mix rate before assembly starts. A segment
   that sounds right on its own is unproven until its rate matches — a raw
   sample can sound right while the assembled mix plays fast.
2. **Resample all segments to one mix rate.** Resample every mismatched
   segment with ffmpeg before assembly; the resampled files are the only
   inputs to the mix. Place them at their resampled durations — do not
   stretch or pad a segment to hide a speed error. Change speaking speed
   only after resampling, by a deliberate speed change on the resampled
   audio, never by leaving silent gaps between bursts.
3. **Verify the assembled mix before delivery.** ffprobe the mix: sample rate
   matches the planned rate, voice duration matches the resampled segments.
   Run a silence scan on the voice track and confirm the longest inter-segment
   silence stays short. Compare assembled duration against expected speech
   duration; stop delivery when voice runs much faster than the script timing
   predicts.
- Prefer generating all voice segments at the mix rate in the first place
  when the voice tool allows it, so resampling becomes a check, not a repair.
