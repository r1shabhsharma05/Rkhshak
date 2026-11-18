# Audit and research

## Channel audit
An audit that lists twenty problems is a way of avoiding the one that matters. This ends in ONE fix.

### Before you write
1. Read the voice profile. If it does not exist, build it from three of the user's own videos.
2. Never invent a number, a result, or a source. If a figure would strengthen it and you do not have one, ask for it or write the line without it.

### What to look at, in this order
1. **The last ten titles, as a set.** Read them as a list, the way the channel page shows them. Do they promise different things? Run them through `scripts/title.py`. A channel where every title is the same shape has a format problem, not a title problem.
2. **The thumbnails, at feed size.** Shrink them. What survives? If three of them are unreadable at that size, that is the fix and nothing else matters yet.
3. **The first fifteen seconds of the three most recent.** Transcribe them and score with `scripts/hookscore.py`. This is where most channels lose.
4. **Upload rhythm.** Not frequency — CONSISTENCY. Six videos in one week and then nothing for a month is worse than one a fortnight forever.
5. **The retention shape**, if they can export it. See `retention-and-edit.md`.

### What to hand back
- The single biggest fix, named, with what to do this week.
- Three things that are already working, so they do not break them. Be specific; "your energy is good" is not an observation.
- What NOT to do yet, and why.

Never open an audit with praise you do not mean, and never end one with a list of twenty things.

## Viral research
Raw view counts rank channel size, not ideas. This ranks by **multiple over each channel's own median** — the only version of the question that is about the video.

```bash
python3 scripts/swipe.py collected.json --min 2.0
```

### Collecting the input
You need at least **four videos per channel** or a median means nothing, and the tool will skip the channel and tell you it did. Collect them however the user prefers — `yt-dlp --flat-playlist -J` against a channel URL is the fastest, the public page works, a manual list works.

```json
[{"channel":"...","title":"...","views":412000,"url":"...","duration":613}]
```

**Read, do not scrape.** Public listings only, never a logged-in session, never the user's own account credentials.

### Reading the output
The multiple is the signal. The formula line is a judgement about the TITLE, matched against the 21 formulas in `scripts/hooks.json` — it is not a claim about why the video worked, and you should say so when you present it.

What to hand back: the top five with their multiples, the formula each used, and the ONE structural thing they share. Then the harder line — which of those the user could actually make this week, in their voice, with what they have.

## The gate
Nothing here publishes. Every output ends in a block the user copies, and the last line of every run is the question: **ship it, or change it?**
