# Retention and edit

## Retention: the only honest feedback YouTube gives you
Almost nobody exports it. Getting the file: Studio → a video → Analytics → Engagement → the audience-retention chart → the download icon → "Audience retention".

```bash
python3 scripts/retention.py retention.csv --duration 600
python3 scripts/retention.py retention.csv --transcript transcript.srt
```

## Three different problems
- **HOOK LEAK** — what is lost in the first 30 seconds. Under 25% is healthy. This is always the first thing to fix, and it is always the first fifteen seconds of script — never the edit.
- **CLIFFS** — single steep drops. A cliff is a moment: a topic change with no signposting, a sponsor read, a long setup. With `--transcript` the tool prints what was being said there, which is what makes the report actionable instead of interesting.
- **SLIDE** — the steady bleed across the middle. A flat slide is pacing. The fix is cutting, not rewriting.

## What to hand back
Name the single biggest leak and one change for it. Not a list of five. Then, only if asked, the rest. And if the hook leak is healthy and the slide is flat, say the video is fine and the problem is packaging — send them to the package workflow.

## Edit decision list
An edit decision list from a timestamped transcript. It prints the cuts. You apply them.

```bash
python3 scripts/deadair.py transcript.srt              # srt, vtt or whisper json
python3 scripts/deadair.py transcript.srt --floor 0.35 --json
```

No transcript yet? Ask for one, or produce one first — `whisper`, `faster-whisper`, or the caption track YouTube generates on an unlisted upload all work. Do not guess at timings.

**What it finds**:
- **DEAD** — gaps longer than the floor, trimmed from the MIDDLE so both sides keep a breath. Cutting flush against speech is what makes a tightened take sound gasping.
- **FILLER** — cues that are nothing but "um", "so yeah", "basically".
- **REPEAT** — a sentence restarted. Compared against the last cue that was actually speech, not the literal previous cue, because most retakes have an "um" between the two attempts.

**What it will not do**: it does not touch media. It has no opinion about B-roll. A 40% cut on the report is a 40% cut of SPEECH — if the video has a long silent demo in it, that number is wrong. Check the report against the footage before trusting the runtime at the bottom.

## Chapters
```bash
python3 scripts/chapters.py transcript.srt --target 8
```

**The rules, which are not optional** — a chapter list that breaks any of these silently does not become chapters at all; the block just sits in the description doing nothing:
- The first entry must be **00:00**.
- There must be **at least three**.
- Each must be **at least 10 seconds** long.

The tool checks all three and tells you when a list is invalid rather than letting you paste it.

**Retitle every line**: `chapters.py` finds the BOUNDARIES well — it scores the pauses you actually took by how much the vocabulary shifts across them. The titles it emits are the topic words, and they are a draft. A chapter called "Thumbnails Titles Packaging" is a placeholder. Rewrite each one as the promise of that section, in the user's voice, three to five words. Chapters are also a retention diagnostic: if a section cannot be named in five words, it is two sections or it is filler.

## The gate
Nothing here publishes. Every output ends in a block the user copies, and the last line of every run is the question: **ship it, or change it?**
