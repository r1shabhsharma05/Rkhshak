# Reference Rebuild — build the exact same thing, measured

When the owner gives a reference — a photo, a video, a link — the job
is not "inspired by" it. The job is the exact same thing, and "exact"
is a measured claim, never a feeling.

## Step 1 — Extract (before any building)
The Researcher (or the Coder, for a visual reference) reads the
reference and writes an extraction note to the board. For a page or
screen:

- **Structure:** sections in order, what each section contains.
- **Layout:** grid, columns, alignment, spacing rhythm, what is above
  the fold.
- **Copy:** every heading, label, and button — transcribed verbatim,
  not paraphrased.
- **Colours:** the palette, sampled — hex values, not "blue-ish".
- **Type:** fonts, sizes, weights, line heights, as observed.
- **Behaviour:** what moves, what opens, what happens on click, hover,
  scroll. If the reference is a video, note the timing.
- **Assets:** images, icons, logos — what they are, where they sit.
- **Unknowns:** anything the reference does not show (a state, a
  screen, a behaviour) — listed, not guessed. Unknowns go to the owner
  as one question, or are marked as the team's best judgement and
  flagged in the final show.

The extraction note is reviewed like research: if the team cannot see
the structure in it, the extraction is redone before building starts.

## Step 2 — Rebuild
The Coder builds from the extraction note, not from memory of the
reference. The plan's steps follow the extraction's section order.
Design rules still apply: `design-unslop` for the UI, `minimal-code`
for the code, `modern-web-guidance` for the web. "Exact copy" means the
visible result matches — it does not mean copying the reference's code,
assets, or brand marks without the right to use them. If an asset
cannot be used lawfully, the Master flags it to the owner before the
build, and the step records the substitute.

## Step 3 — Side-by-side diff check
The Verifier puts the rebuild next to the reference and checks each
dimension, one by one. The check is done on the rendered result, not
on the source:

| Dimension | What is compared |
|---|---|
| Layout | Section order, columns, alignment, spacing, fold |
| Copy | Every heading, label, button — verbatim match |
| Colours | Sampled hex values against the extraction note |
| Type | Font, size, weight, line height |
| Spacing | Gaps, padding, margins — measured, not eyeballed |
| Behaviour | Click, hover, scroll, animation — same trigger, same result |
| Assets | Every image/icon present, same place, same size |
| Responsive | The same checks at the reference's breakpoints |

The Verifier posts a diff report:
```
REFERENCE DIFF — <step or page>
MATCH: <dimensions with zero diff>
DIFFS:
  1. <dimension> — <what differs> — <cause, if known>
  2. ...
REMAINING: <count>
```
- **Fix until the diff is zero**, or until each remaining diff is
  named with its cause (e.g. "asset unavailable — substitute used",
  "font not licensed — closest match used").
- **Never claim "exact, no diff" without the diff check.** A rebuild
  that has not been diff-checked is "unverified", not "exact". The
  Master never shows the owner an "exact" claim that the diff report
  does not support.
- Each fix round re-runs the full diff check, not just the fixed
  dimension — a fix in one place can break another.

## What the owner is shown
The diff report, with the final count. "Zero diffs" or "3 diffs
remaining, each named with its cause" — both are honest outcomes, and
the owner decides whether the remaining diffs are acceptable. A
rebuild is never presented as finished while its diff report says
otherwise.
