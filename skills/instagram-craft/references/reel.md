# Reel

Turns one raw idea into a Reel somebody finishes. A Reel is decided in the first two seconds and kept by the next five.

## Tools (run them — do not eyeball the hook or guess at the length)
```bash
python3 scripts/reel-hookscore.py hooks.txt              # rank hook options
python3 scripts/reel-hookscore.py --hook "one line"      # score a single one
python3 scripts/reel-beats.py script.txt --target 30     # timed beat sheet before shooting
```

## Before you write
1. Read the voice profile. If it does not exist, build it from three of the user's own Reels.
2. Read `scripts/reel-hooks.json`: 26 formulas, each with a template, a filled example, the on-screen version, what it is for, and how it gets ruined.
3. If the idea is thin, do not pad it. Ask one batched question: what happened, to whom, and what did it cost or return. A Reel needs one specific true thing.
4. If the swipe file exists, read it. It beats the defaults in this skill.

## The 26 hook formulas (ids and names)
1 Cost Confession · 2 Negative Command · 3 Nobody Tells You · 4 The Replacement · 5 Time Collapse · 6 The Receipt · 7 Wrong Way, Right Way · 8 Insider Leak · 9 The Steal · 10 If This, Then Watch · 11 Numbered With A Favourite · 12 The Objection · 13 Before And After, On Screen · 14 The Callout · 15 The Flop Record · 16 The Verbatim Question · 17 Head To Head · 18 Cold Open Demo · 19 The Deadline · 20 Permission · 21 Mid-Sentence Start · 22 Contrarian Flip · 23 The Statistic · 24 The Reveal · 25 Someone Else's Result · 26 The Superlative. Templates, examples, and ruin-modes live in `scripts/reel-hooks.json` — read the entry for each formula you use, do not guess its shape.

## The shape
```
0:00–0:02  HOOK       the claim. Spoken line and on-screen line, written separately. Motion in the first frame, not a static face.
0:02–0:07  THE STAKE  why this matters to the person watching. One line.
0:07–...   THE BODY   one idea per beat; the frame changes every beat.
LAST 3s    THE PAYOFF deliver what the hook promised, then the single ask.
LAST LINE  THE LOOP   echo one word from the hook so the replay lands clean.
```
Length: 15–45 seconds is the working range. Reels run to 3 minutes and almost nobody should use it. Under 7 seconds the loop counts inflate and nothing else does.

## The loop
1. **Pick three hooks, not one.** Three formulas that genuinely fit the idea; spoken line plus on-screen line for each. Different formulas, not three rewrites of one.
2. **Score them.** One hook per line in a file, run `reel-hookscore.py`, show the ranking. If the top one is under 50, there is no hook yet — no amount of editing fixes that.
3. **Write the script** on the winning hook. Plain spoken language, the way the user talks. Contractions. Short lines. No sentence they would have to rehearse.
4. **Time it.** Run `reel-beats.py` at the target length. Fix every flag: a hook past 3 seconds, any beat over 4 seconds, a run of beats with nothing concrete, no loop. Re-run until clean.
5. **Humanise it** (see `human-voice.md`) before showing it. A written-sounding line is obvious the moment someone says it out loud.
6. **Print the block**: the script in a fenced block, on-screen text as a separate list with timings, then the receipt:
```
REEL READY
hook:       #3 Nobody Tells You, scored 86 STRONG
length:     28.4s across 9 beats at 165 wpm
on-screen:  6 cards
humanizer:  4 artefacts stripped, human score 81 PASS
caption:    run the caption workflow next
```
7. **Never publish.** On "yes", append to `~/.claude/instagram/log.md` (date, hook formula, first line) so the audit has a history later.

## On-screen text is a separate script
- ≤ 6 words per card. It is read at arm's length by someone who is not listening yet.
- The hook card is up at frame 1, not after a beat of silence.
- Keep it inside the safe zone: on 1080×1920, nothing above y=230 or below y=1440, and keep the right 230 pixels clear. The interface sits on top of everything outside that box.
- Never put the hook where the caption sits (bottom of the frame — it is covered).
- Burn in captions for the body. Most people watch muted first.

## Rules that make the difference
- **One idea per Reel.** Two ideas is two Reels. Say so.
- **Numbers over adjectives.** "$4,200" beats "a lot". If no number was given, ask for one rather than writing around the hole.
- **Cut the intro.** No greeting, no "in this video", no name, no logo sting. The video starts at the sentence normally reached at second six.
- **Change the frame every beat.** A static shot for 8 seconds is where people leave.
- **One ask at the end.** Comment a keyword, save it, or follow. One.
- **Never fabricate.** No invented metrics, clients, revenue, or outcomes — even as a placeholder. Leave `{{your number}}` and flag it.
- **Do not write around trending audio the user cannot use.** If the idea needs the user's own voice, say so.
