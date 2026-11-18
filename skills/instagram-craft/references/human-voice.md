# Human voice

Strip the machine fingerprint out of any draft — and score it against a five-check detection panel before it goes out. Captions are short and scripts get said out loud: a written-sounding line in a 600-character caption is a larger share of the text than the same line in an essay, and a voiceover nobody could say naturally is obvious in the first take. The tell is not a detector flagging the post — it is a person scrolling past something that reads like a brand, or a creator stumbling over their own script.

## Tools (use them — do not eyeball this)
```bash
python3 scripts/humanize.py draft.txt --report        # clean it, show what changed
python3 scripts/detect.py draft.txt                    # score it, five checks
python3 scripts/detect.py before.txt after.txt         # prove the delta
```
Both read `scripts/slop.json`: stock words and phrases with plain-English replacements, invisible character classes, typographic substitutions, and structural tells. The last block of each list is Instagram-specific — vocabulary that only shows up in captions and voiceovers. It is meant to be edited: if the user has a word they always use that the lexicon strips, take it out of the file.

## What gets fixed automatically
1. **Invisible characters.** Zero-width spaces and joiners, word joiners, soft hyphens, byte-order marks, Unicode tag characters, invisible separators, non-breaking and narrow spaces. A keyboard does not produce these. They survive copy-paste, are invisible in every editor, and are the most mechanical thing in generated text. `humanize.py` deletes every one, including any remaining Unicode format character it does not have a name for.
2. **Typography.** Em dash to comma, en dash to hyphen, curly quotes to straight, ellipsis to three dots, bullet character to hyphen. The em-dash pass is the one that matters: it collapses the dash to a comma and cleans up the double punctuation and orphaned periods that leaves behind.
3. **The slop lexicon.** Stock words (delve, leverage, robust, seamless, crucial, "testament to", "in today's fast-paced world") plus the Instagram block ("stop scrolling", "in today's video", "follow for more", "tag someone who needs this", "the algorithm loves", "run don't walk"). Each swapped for a plain word or deleted, capitalisation preserved, URLs untouched.

## What does NOT get fixed automatically
Structural tells get **flagged, not rewritten**, because changing the shape of a sentence needs judgement: "It's not just X, it's Y" and "not only X but also Y"; rule-of-three triads; rhetorical one-word question lines ("The result?"); the video preamble ("in this video I'm going to show you"); emoji bullet lists; three or more shouted words in a row; hashtag walls; reflex bait ("follow for more", "tag someone who", "double tap if"). That list is the writer's job: rewrite each flagged line by hand, keeping the meaning, then re-run `detect.py`. This is the part that moves the score from REVIEW to PASS, and a script cannot do it.

## The five checks
`detect.py` scores five signals 0–100 (higher is more human):
| Check | What it measures | Machine looks like |
|---|---|---|
| BURSTINESS | Sentence-length variation | Every sentence the same length |
| SPECIFICITY | Numbers, names, concrete markers per 100 words | Abstract nouns, no figures |
| SLOP DENSITY | Lexicon hits per 100 words | Stock vocabulary |
| FINGERPRINT | Invisible chars, em dashes, curly quotes per 1k chars | Typographically perfect |
| VOICE | Contractions, person, structural tells | No contractions, staged reveals |

The verdict weights the mean at 60% and the **weakest single check** at 40%, because one signal is enough. PASS needs an overall of 70+ with no check below 55.

## Say this honestly
These are five local heuristics modelled on the signals public detectors key on. They run entirely on the user's machine and nothing is uploaded. They are **not** GPTZero, Originality, Copyleaks, Winston, or Turnitin; they do not call those APIs and cannot promise those verdicts. Fixing what they measure does tend to move those numbers, because they measure the same underlying things. That is the claim. Do not make a bigger one on the user's behalf, and do not tell a user their text is undetectable.

## Order of operations
1. `humanize.py draft.txt -o clean.txt --report`. 2. Read the structural flags; rewrite those lines by hand. 3. `detect.py draft.txt clean.txt` to show before and after. 4. If the verdict is not PASS, fix the weakest check named in the output and go again. Two rounds is normal. Five means the draft was written by formula, and the fix is a different draft, not more passes. 5. Show the user the cleaned text and the score. Never the score alone.
