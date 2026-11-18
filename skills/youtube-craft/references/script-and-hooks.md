# Script and hooks

One idea into a script somebody finishes.

## Tools (run them — do not eyeball the hook)
```bash
python3 scripts/hookscore.py hooks.txt              # rank hook options
python3 scripts/hookscore.py --hook "one line"      # score a single one
```

## Before you write
1. Read the voice profile. If it does not exist, build it from three of the user's own videos.
2. Never invent a number, a result, or a source. If a figure would strengthen the script and you do not have one, ask for it or write the line without it.

## The 21 hook formulas
The Statistic · Someone Else's Result · The Mistake · Contrarian Flip · The Reveal · The Superlative · The Clock · I Tried It · The Question · Before and After · The Teardown · The Stack · The Warning · The List · The Receipt · The Insider · The Impossible Claim · The Comparison · The Origin · The Deadline · The Direct Address. Templates and examples live in `scripts/hooks.json` — read the entry for each formula you use.

## The shape
**The first 15 seconds is the whole job.** It does three things or the video leaks: confirm the click the title promised, open a question the viewer cannot close, and prove the payoff exists.

1. **Hook.** Write FIVE against the 21 formulas, run them through `hookscore.py`, keep the top two, and show the user both with their scores. Never hand over one hook.
2. **The turn** (0:15–0:45). Say what the video is going to do, in one sentence, and start doing it. No channel intro, no "before we get started", no subscribe pitch. Those are the single most common cause of the 0:30 cliff.
3. **The body.** One idea per beat. Mark each beat with what is ON SCREEN, not just what is said — a talking head with nothing to look at is a podcast.
4. **The payoff.** Deliver the thing the hook promised, explicitly, and say that you are delivering it: "that is the prompt, it is in the description".
5. **The close.** One ask. Not three.

## What to hand back
- The two best hooks with their scored panels.
- The script, beat by beat, with `[ON SCREEN: …]` on every beat.
- The runtime estimate at 150 words per minute.
- One line naming which formula the winning hook used and why it fits this idea.

## The gate
Nothing here publishes. Every output ends in a block the user copies, and the last line of every run is the question: **ship it, or change it?**
