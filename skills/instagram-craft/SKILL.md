---
name: instagram-craft
description: "Plan, write, and review Instagram content — weekly plans, Reels from a raw idea (26 hook formulas, scored, timed beat sheet), carousels, captions, Stories, profile scoring, comments and DMs, repurposing long assets, and post-mortem audits ranked by what actually worked. Draft and schedule only: nothing is posted, published, liked, followed, or messaged by this skill. The user posts everything by hand, or through Instagram's own tools. Use when the user asks about Instagram, Reels, carousels, captions, hashtags, Stories, their profile, comments, DMs, or what is working in their niche."
---

# Instagram Craft — write it well, post it yourself

## Purpose
Instagram rewards one specific thing at a time and punishes everything else: a Reel lives or dies in its first two seconds, a carousel earns the swipe or it does not, a profile answers one question in three seconds. This skill plans the week from the user's own evidence, writes each format to its own rules, scores the draft before the user shoots it, and audits what already went out — so the next week is built on what worked, not on defaults.

## The standing rule (owner's order — never soften it)
**Draft, schedule, and craft only. Never auto-post live.** Instagram auto-posting is stopped on the owner's order. Nothing in this skill posts, publishes, schedules into a live slot, likes, follows, comments, or sends a DM. Every output ends as a copy-ready block the user posts by hand — or, for keyword replies only, through Instagram's own tools or an approved partner. If the user says "post this now", that is a fresh explicit instruction for that one post, not a change to this rule.

## When NOT to use
- To scrape Instagram, log in on the user's behalf, or ask for a password. If a page needs a login, the user — already logged in — drives their own browser, or pastes the content.
- To automate engagement at volume. Automated comments, bulk DMs, and crawlers violate Instagram's Terms of Use and get accounts action-blocked. Reading ten accounts at human speed is research; building a crawler is not.
- To invent numbers, clients, revenue, or outcomes under the user's name — even as placeholders. Unknown numbers stay as `{{your number}}` and are flagged.

## Multi-agent roles (never one agent doing all three)
| Role | Job | Must NOT do |
|---|---|---|
| **Planner** | Build the week from the voice file, swipe file, and log. | Write the posts. |
| **Writer** | Draft one format at a time, run the linters, score the hook. | Publish anything. Review its own draft as final. |
| **Auditor** | Read the account's own insights and say what worked, with the numbers shown. | Recommend from defaults when the data says otherwise. |

One agent per role. If only one agent is available, it drafts only and reports — it does not approve its own work.

## Workflow — plan the week
`references/plan-and-voice.md`: once a week, same day. Read the voice profile, swipe file, and log if they exist; otherwise ask four things (what they sell and to whom, 3–4 themes, what actually happened this week, 10 accounts worth being visible to). 4–5 posts a week, at least 3 Reels; mix Proof / Teach / Opinion / Story / Offer, never two of the same type back to back. Post when the audience is awake — and say plainly that the hour matters far less than the first two seconds. Daily 20-minute engagement round (5 reach / 3 peers / 2 buyers), before posting. Output is a plan, never a schedule: nothing is scheduled or posted anywhere.

## Workflow — Reel
`references/reel.md`: read the voice profile first; pick three hooks from different formulas in `scripts/reel-hooks.json` (26 formulas); score them with `scripts/reel-hookscore.py` — under 50, there is no hook yet; write the script on the winner in plain spoken language; time it with `scripts/reel-beats.py` (15–45s working range, hook inside 3s, no beat over 4s); humanise it; print the block with the REEL READY receipt. On-screen text is a separate script: ≤ 6 words per card, hook card at frame 1, inside the safe zone (nothing above y=230 or below y=1440 on 1080×1920, right 230px clear). One idea per Reel; numbers over adjectives; no greeting, no intro; one ask at the end; loop line echoes the hook.

## Workflow — carousel and caption
`references/carousel-and-caption.md`: carousels for ideas with sequence that need re-reading (6–10 slides, 1080×1350, cover ≤ 6 words, slide 2 is a second cover, one idea per slide, recap slide, one CTA). Captions: decide Job A (the Reel carries the hook — caption is the ask + context + search terms) or Job B (the caption is the content — line 1 is the hook); 125 visible characters; one ask; up to 5 hashtags, specific, as labels; search terms as phrases humans type; no link in the caption; lint with `scripts/caption.py`.

## Workflow — Stories
`references/story.md`: 3–7 frames a day; face or hand in frame 1; one idea per frame; text inside the middle (nothing above y=250 or below y=1600); the ask at frame 4, not frame 7; one sticker with a job (poll for volume, question box for verbatim language, quiz for misconceptions, link only where there is somewhere real to go). Sell on Stories, not in posts. The DM funnel is: they act first (vote, reply, question box), then the user replies. Never the reverse.

## Workflow — engagement (comments, replies, DMs)
`references/engagement.md`: comments on others' posts — 9 types, two options of different types, never generic, never a pitch, early beats late. Replies under the user's own posts — triage first (KEYWORD / LEAD / SUBSTANCE / QUESTION / SUPPORT / NOISE), answer in public, a repeated question becomes a Reel. DMs — only three kinds worth writing (reply to a hand raised, warm approach, specific collab pitch); keyword delivery sends the thing first, no gate; two follow-ups (+4 days with something new, +10 days closing the loop), then stop.

## Workflow — profile
`references/profile.md`: score 0–100 against the 12-item rubric in `scripts/profile-rubric.json` (name field, bio lines, pinned three, highlights, link, grid, photo, handle). Fix in descending order of points lost. Re-score honestly — if the rewrite reaches 84 and not 98, say 84.

## Workflow — audit and research
`references/audit-and-research.md`: the account's own last 30 posts are the evidence. Rank by outlier multiple (views ÷ account median) and sends per reach — not raw views. A reel with 4,000 views and 90 sends beat one with 60,000 views and 11. Views with no follows is a profile problem; no views is a hook problem — separate them before recommending anything. Research (`scripts/swipe.py`): 6–12 accounts within ~10× the user's size, rank by outlier multiple above 3×, copy the formula never the video, attribute every row. State sample size and confidence plainly — 40 reels across 6 accounts supports a claim; 12 does not.

## Workflow — repurpose
`references/repurpose.md`: read the whole long asset, extract claims, numbers, stories, mechanisms, mistakes, quotable lines — with counts — before writing anything. Claims/mistakes/stories → Reels; mechanisms/lists → carousels; quotable lines → Story frames. Each post stands alone; the viewer has never seen the source. One at a time, each through the Reel workflow and the humaniser. If the asset yields fewer than 4 items, say it is thin.

## Workflow — humanise everything
`references/human-voice.md`: run `scripts/humanize.py` (strips invisible characters, typography, slop lexicon) and `scripts/detect.py` (five checks: burstiness, specificity, slop density, fingerprint, voice; PASS needs 70+ overall with no check below 55). Structural tells are flagged, not rewritten — rewriting them is the writer's job. These are local heuristics, not GPTZero or any commercial detector — never claim a verdict those tools would give, and never tell a user their text is undetectable.

## Scripts (in `scripts/`)
| File | What it does |
|---|---|
| `reel-hooks.json` | 26 Reel hook formulas with templates, examples, and how each gets ruined |
| `reel-hookscore.py` | Score hook lines; rank options |
| `reel-beats.py` | Time a script into a beat sheet at a target length |
| `caption.py` | Lint a caption: visible 125 chars, asks, hashtags, keywords |
| `humanize.py` / `detect.py` / `slop.json` | Strip the machine fingerprint; score five human-voice checks |
| `swipe.py` | Rank collected reels by outlier multiple; name the hook formula |
| `profile-rubric.json` | 12-item profile rubric, 100 points |

## References
| File | What it covers |
|---|---|
| `references/plan-and-voice.md` | Weekly plan, voice profile, log and swipe files, engagement round |
| `references/reel.md` | Reel shape, hook formulas, script, beats, on-screen text, rules |
| `references/carousel-and-caption.md` | Carousel structure and files; caption jobs, hashtags, search terms, linter |
| `references/story.md` | Daily Stories shape, stickers, DM funnel |
| `references/engagement.md` | Comments on others, replies under your own posts, DMs and follow-ups |
| `references/profile.md` | Profile scoring rubric and rewrite order |
| `references/audit-and-research.md` | Post-mortem audit metrics; viral research and the swipe file |
| `references/repurpose.md` | Extracting posts from one long asset |
| `references/human-voice.md` | Humaniser, detection panel, what the tools do and do not prove |

## Rules
- **Nothing is posted by this skill.** Ever. Copy-ready blocks only; the user posts by hand.
- **Never fabricate.** No invented metrics, clients, revenue, or outcomes. Unknown numbers stay as `{{your number}}`.
- **Voice first.** Read the voice profile before writing; if none exists, build it from three of the user's own Reels. A script in the wrong voice is unusable.
- **Run the tools, do not eyeball.** Hook scores, beat sheets, caption lint, humaniser scores — the scripts exist because judgement alone misses these.
- **One ask.** One ask per Reel, caption, carousel, DM, and Story sequence. Two asks is the same as none.
- **Evidence over defaults.** The swipe file and the audit outrank every rule in this skill when they disagree — say so when they do.
- **No login, no scraping.** Never log into Instagram for the user, never ask for a password, never build a crawler.

## Provenance
Distilled in our own words from the 13 ig-* sources (no LICENSE file present in the source dirs). Scripts and JSON data (hook formulas, scorers, caption linter, swipe tool) are copied as functional assets with their original headers intact; two minimal path patches only. Nothing is posted by this skill — copy-ready blocks only.

## Report format
What was made (format + hook formula + length) · scores (hook, beats, humaniser, caption lint) · the copy-ready block · what the user does next (shoot it / post it / say "write Tuesday").
