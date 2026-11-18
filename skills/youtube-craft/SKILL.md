---
name: youtube-craft
description: "Plan, write, package, and review YouTube videos — weekly plans sized to the creator's real capacity, scripts from a raw idea (21 hook formulas, scored, retention beats marked), title and thumbnail as one pairing, description/tags/search text, chapters, edit decision lists from transcripts, retention diagnosis, Shorts cut from long videos, and channel audits and viral research ranked by how far each video beat its own channel. Draft only: nothing is published, uploaded, or posted by this skill. The user publishes everything. Use when the user asks about YouTube, a video script, titles, thumbnails, CTR, retention, chapters, Shorts, or why a channel is not growing. For YouTube search text, this skill owns it; for website SEO, use the seo skill."
---

# YouTube Craft — write it well, publish it yourself

## Purpose
A YouTube video is won in three places: the first fifteen seconds (does the viewer stay?), the packaging (does anyone click?), and the plan (does the channel ship on a rhythm it can keep?). This skill plans the week around what is already half-made, writes the script from scored hooks, lints the title and thumbnail as one unit, diagnoses retention from the graph rather than from feelings, and audits the channel down to one fix — the single biggest one, named, with what to do this week.

## The standing rule
**Draft only. Nothing is published by this skill.** Every output ends in a block the user copies, and the last line of every run is the question: **ship it, or change it?** The user uploads, publishes, replies, and pins. If the user says "publish this now", that is a fresh explicit instruction for that one video, not a change to this rule.

## When NOT to use
- To promise views, subscribers, or a timeline. No outcome is ever guaranteed; report what was measured and what it usually correlates with.
- To scrape YouTube with a logged-in session or the user's credentials. Public listings only — `yt-dlp --flat-playlist` against a channel URL, the public page, or a manual list.
- To invent numbers, results, or sources. If a figure would strengthen a script and you do not have one, ask for it or write the line without it.

## Multi-agent roles (never one agent doing all three)
| Role | Job | Must NOT do |
|---|---|---|
| **Planner** | Build the week from capacity and what is half-made. | Write the scripts. |
| **Writer** | Draft one video at a time, score the hooks, lint the packaging. | Publish anything. Review its own draft as final. |
| **Auditor** | Read retention, titles, and the first fifteen seconds; name one fix. | Hand back a list of twenty problems. |

One agent per role. If only one agent is available, it drafts only and reports — it does not approve its own work.

## Workflow — plan the week
`references/plan-and-voice.md`: ask two questions before writing anything — how many hours do you actually have, and what is already half-made? One anchor (the video the week is for, on the day the channel's own analytics say is best — ask for that, do not assume a day), one cheap one (built from something that exists), three Shorts cut from the anchor. Three uploads on a seven-day week, not seven. Hand back a table (day, format, working title, the one sentence it promises, what already exists for it) plus the honest line at the bottom: how many hours this costs, and what to drop first if the week goes wrong.

## Workflow — script
`references/script-and-hooks.md`: read the voice profile first (build it from three of the user's own videos if it does not exist). Write FIVE hooks against the 21 formulas in `scripts/hooks.json`, run them through `scripts/hookscore.py`, keep the top two, show both with scores. Never hand over one hook. The first 15 seconds must confirm the click, open a question the viewer cannot close, and prove the payoff exists. Then the turn (0:15–0:45, one sentence, then start doing it — no channel intro, no "before we get started", no subscribe pitch), the body (one idea per beat, `[ON SCREEN: …]` on every beat), the payoff (deliver what the hook promised, explicitly), the close (one ask). Runtime estimate at 150 words per minute.

## Workflow — package and search text
`references/package-and-seo.md`: title and thumbnail are ONE unit — the thumbnail must not repeat the title. Generate ten titles, run them all through `scripts/title.py`, show the top three with scores and the specific issue on each. Rules the tool enforces: 60 characters is the desktop truncation, 40 is mobile home feed; three words maximum on the thumbnail; a number, a name, or a date beats every adjective; two all-caps words is the ceiling before a title reads as spam. For the winner, write the thumbnail brief (expression, framing, three words, background contrast at feed size). Description: first two lines carry the search snippet; then the link or resource; then chapters; then the long version. Tags are a weak signal — use them for disambiguation (spellings, tool names, abbreviations), fifteen is plenty, never stuff unrelated ones. Query test: write the three search queries the video should win, and check the title and first two description lines contain the words in those queries. If they do not, the problem is the title, not the description. Search is a smaller lever than packaging and a bigger one than people think for evergreen videos; for a subscriber-feed video, say so and spend the effort on packaging instead.

## Workflow — retention and edit
`references/retention-and-edit.md`: read the Studio audience-retention export with `scripts/retention.py` — three different problems (HOOK LEAK: what is lost in the first 30 seconds, under 25% is healthy, always fixed in the first fifteen seconds of script, never the edit; CLIFFS: single steep drops, a moment — topic change with no signposting, a sponsor read, a long setup; SLIDE: steady bleed across the middle, fixed by cutting, not rewriting). Name the single biggest leak and one change for it. If the hook leak is healthy and the slide is flat, the video is fine and the problem is packaging. Edit decision lists from a transcript with `scripts/deadair.py` (dead air, filler cues, retakes, timecodes — trimmed from the middle so both sides keep a breath). Chapters with `scripts/chapters.py`: first entry 00:00, at least three, each at least 10 seconds — a list that breaks any of these silently becomes nothing at all. Retitle every chapter as the promise of its section, 3–5 words.

## Workflow — Shorts
`references/shorts-and-repurpose.md`: a Short is not a clip of the best moment — it is a moment that survives without the video around it. Find spans of 20–55 seconds that open on a complete thought, contain a turn (a claim, then something that complicates or proves it), and end on a line, not a trail-off. Show the top five with timecodes and first lines. Each one gets a NEW first line (run through `hookscore.py`), on-screen text for the first two seconds in different words from the spoken line, a loop point, and a vertical-framing note.

## Workflow — audit and research
`references/audit-and-research.md`: audit ends in ONE fix. Read the last ten titles as a set (run them through `title.py` — same shape everywhere is a format problem, not a title problem), the thumbnails at feed size (three unreadable at that size is the fix), the first fifteen seconds of the three most recent (transcribe, score with `hookscore.py`), upload rhythm (consistency, not frequency — six videos in one week then nothing for a month is worse than one a fortnight forever), and the retention shape if exportable. Hand back the single biggest fix, three things already working (specific — "your energy is good" is not an observation), and what NOT to do yet. Research with `scripts/swipe.py`: at least four videos per channel or the median means nothing; rank by multiple over each channel's own median; the formula line is a judgement about the TITLE, matched against the 21 formulas — not a claim about why the video worked, and say so.

## Scripts (in `scripts/`)
| File | What it does |
|---|---|
| `hooks.json` | 21 YouTube hook formulas |
| `hookscore.py` | Score hook lines (five properties, weakest-link verdict) |
| `title.py` | Lint a title + thumbnail pairing; rank title lists |
| `retention.py` | Read a retention CSV; name hook leaks, cliffs, slides |
| `deadair.py` | Edit decision list from a transcript (SRT/VTT/whisper JSON) |
| `chapters.py` | Chapters from a transcript, validated against YouTube's rules |
| `swipe.py` | Rank collected videos by multiple over channel median; name the formula |

## References
| File | What it covers |
|---|---|
| `references/plan-and-voice.md` | Weekly plan, voice profile, capacity honesty |
| `references/script-and-hooks.md` | Script shape, 21 hook formulas, scoring, retention beats |
| `references/package-and-seo.md` | Title + thumbnail as one unit; description, tags, query test |
| `references/retention-and-edit.md` | Retention diagnosis, edit decision lists, chapters |
| `references/shorts-and-repurpose.md` | Shorts from long video; what survives without context |
| `references/audit-and-research.md` | Channel audit (one fix); viral research by channel-relative multiple |

## Rules
- **Nothing is published by this skill.** Copy-ready blocks only; the user publishes.
- **Never fabricate.** No invented numbers, results, or sources. Ask, or write the line without the figure.
- **Voice first.** Read the voice profile before writing; build it from three of the user's own videos if it does not exist. A script in the wrong voice is worse than no script.
- **Run the tools, do not eyeball.** Hook scores, title lint, retention reads, chapter validation — the scripts exist because judgement alone misses these.
- **One ask.** One ask per video, per Short, per description. Not three.
- **Retention is the only honest feedback.** A feeling about a video is not evidence; the graph is. If the graph was not exported, say what is being guessed.
- **Read, do not scrape.** Public listings only, never a logged-in session, never the user's credentials.

## Provenance
Distilled in our own words from the 11 yt-* sources (no LICENSE file present in the source dirs). Scripts and JSON data (hook formulas, scorers, title linter, retention and chapter tools) are copied as functional assets with their original headers intact; one minimal path patch only. Nothing is published by this skill — copy-ready blocks only.

## Report format
What was made (format + hook formula + runtime) · scores (hook, title lint, retention) · the copy-ready block · ship it, or change it?
