# Karpathy Guidelines — distilled

Four behavioural rules for coding agents, distilled in own words from Andrej Karpathy's observations on common LLM coding mistakes: https://x.com/karpathy/status/2015883857489522876

Source skill: `karpathy-guidelines` (MIT, multica-ai/andrej-karpathy-skills). Merged here as a reference, not a new skill — two of the four principles are new to this skill; the other two already live in the refs below, so they are mapped, not repeated.

## The two rules this skill did not already have

### 1. Ask before coding — don't guess, don't pick silently

Before writing any code, state your assumptions in one line. If anything is unclear, stop and ask. If the request has more than one plausible reading, present the readings — never choose one silently. If a simpler approach exists than the one asked for, say so and push back. Confusion hidden behind a confident guess becomes wrong code; a one-line question up front is cheaper than a rewrite.

This is a bias toward caution over speed. For a trivial, unambiguous task, use judgment — don't interrogate the user over nothing.

### 2. Define "done" per step, then loop until verified

Turn each step into a check you can run. "Add validation" becomes "write tests for invalid inputs, then make them pass". "Fix the bug" becomes "write a test that reproduces it, then make it pass". "Refactor X" becomes "tests pass before and after". For a multi-step task, list each step with its check:

```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
```

A step is done only when its check passes. Never claim a step done on a feeling — "make it work" is not a success criterion, and a weak criterion means constant clarification later.

## The two principles already covered here (mapped, not repeated)

- **Simplicity first — minimum code, nothing speculative.** Already enforced by `references/yagni.md` (build only what today needs), `references/abstraction-judgment.md` (no abstraction for single-use code), and `references/ponytail.md` (the decision ladder). If the code could be half as long, rewrite it — the senior-engineer test is: would a senior call this overcomplicated?
- **Surgical changes — touch only what you must.** Already enforced by `references/smallest-change.md` (every changed line traces to the one-sentence change) and `references/delete-first.md` (clean up only the mess your own change made — remove imports, variables, and functions your change orphaned; mention unrelated dead code, don't delete it). Don't "improve" adjacent code, comments, or formatting; match the existing style even if you would do it differently.

## The test

Before coding: can you state your assumptions and what "done" means for the first step? If not, ask first. After coding: does every changed line trace to the request, and does every step have a check that passed? If not, it isn't done.
