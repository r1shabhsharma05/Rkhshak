# Audit and research

## Post-mortem audit
The only honest source of what works for an account is that account. Every rule in every Instagram guide — including this skill — is a prior. The user's own last 30 posts are the evidence.

**Input**: insights per post (views, reach, interactions, watch time, saves, shares, follows, non-follower share of reach — screenshots are fine), or the retention graph for the best and worst recent Reels (worth more than the rest combined), or just the posts and their view counts (enough for a first pass). Also read the log if it exists — it records which hook formula each post used.

**What to actually measure** — raw views is the least useful number, because it is mostly a function of how many people already follow the account. Compute these instead and show the working:
| Metric | How | What it tells you |
|---|---|---|
| Outlier multiple | views ÷ the account's own median views | Whether this was a real hit or a normal day |
| Non-follower reach | % of reach from non-followers | Whether it travelled at all |
| Hold at 3s | viewers still there at 3s ÷ viewers who started | Whether the hook worked — the hook's grade |
| Average watch time | straight from insights | Whether the middle worked |
| Sends per reach | shares ÷ reach | The strongest single signal — a send is a person putting their name on it |
| Follows per reach | follows ÷ reach | Whether the profile converted the attention |

Rank by outlier multiple and sends per reach, not views. A Reel with 4,000 views and 90 sends beat one with 60,000 views and 11.

**Then find the pattern** — top five vs bottom five side by side: hold at 3 seconds (if the top and bottom differ here, it is the hook and nothing else); hook formula (which ids from `scripts/reel-hooks.json` are in the top five); format; length (under 15s, 15–30s, 30–60s, over 60s); theme; whether the user replied to comments in the first hour; day and time — check this **last** and only if the others show nothing. It is almost never the cause, and it is where people want it to be.

State the finding as a claim with the evidence attached, and say how confident it is. With 30 posts you can see a pattern. With 6 you cannot — saying so is better than inventing one.

**The distinction that saves people months**: a Reel that gets views and no follows is not a failed Reel, it is a profile problem. A Reel that gets no views is a hook problem. Separate the two before recommending anything. If non-follower reach is high and follows per reach is low, stop rewriting hooks and go to the profile workflow.

**Output**: audit block (post count, date range, median views; top 5 and bottom 5 by outlier multiple with the six metrics; what the data says, numbered, each with its evidence; STOP list; DO MORE list). Then hand the conclusions to the plan workflow (next week built on the user's own evidence) and to the research workflow (swipe file filtered to the formulas that work for this account).

## Viral research (the swipe file)
The research workflow. Everything else in this skill writes; this one goes and looks. Run it monthly, not daily — formulas last a season.

**The one idea**: raw views are not evidence. An account with two million followers doing 400,000 views had a quiet Tuesday. An account with four thousand followers doing 400,000 views found something, and that something is copyable. Everything ranks on the **outlier multiple** (views ÷ that account's own recent median). Above 3× is a signal; below 1.5× is that account's normal day. Collect accounts **within about 10× of the user's own size** — a formula that works at 2M followers often works because it is at 2M followers.

**Step 1 — pick the accounts**: ask the user for 6–12, or propose them and get approval: 4 direct (same niche, same offer, slightly ahead), 4 adjacent (different niche, same audience — where formats get borrowed from before anybody in the niche has them), 2–4 outsized (much bigger, for format only, never cadence or tone). Also ask them to open their own Saved collection — the fastest, most relevant corpus that exists, already filtered by their taste.

**Step 2 — go and look**: use whatever browsing the session actually has. There is no API for this and there does not need to be — the volume is small enough to read. Rules that are not negotiable: never log into Instagram on the user's behalf and never ask for a password (if a page needs a login, the user drives their own browser, or pastes); this is reading, not scraping — ten accounts, a dozen Reels each, at human speed (no crawler, no scraping service, no background loops); copy the formula, never the video (hook shape, structure, length, cut pattern — not their script, voice, or edit), and attribute every row to the account it came from. Capture per Reel: account, followers, median (eyeball the last 12 Reels, take the middle view count), views, hook (first line, verbatim), on-screen text, length, CTA. Median is the important one — without it, you are back to ranking by follower count.

When Instagram will not show enough, the same hook grammar runs on YouTube Shorts, where view counts and transcripts are public and no login is involved — a legitimate second corpus.

**Step 3 — rank it**: fill a tab-separated file (account, followers, median, views, hook) and run:
```bash
python3 scripts/swipe.py captured.tsv --out ~/.claude/instagram/swipe.md
```
It computes the outlier multiple, names the hook formula using the same 26 formulas the Reel workflow writes from, scores each hook, and prints what separates the top third from the bottom third.

**Step 4 — say what it means, carefully**: three things and no more — which formulas over-index in the top third (two formulas appearing four times each across six accounts is a finding; one appearing twice is not); what the top third share structurally that the bottom third do not (hook length, visual payoff, first-frame motion, where the ask is); the unclassified rows (every hook the classifier could not name is noise or a formula not in the file yet — read them by hand; the most valuable column in the output). Then state the sample size and confidence in plain words. Forty Reels across six accounts supports a claim. Twelve does not.

**Step 5 — turn it into something to shoot**: for the top three formulas, write the user's version — their own story, their own number, in the shape that is working. Hand each one to the Reel workflow with the formula id already chosen. Never hand back "make a Reel like this one". Hand back a hook line they could say tomorrow.

Nothing is posted, followed, liked, or messaged by this skill. It reads.
