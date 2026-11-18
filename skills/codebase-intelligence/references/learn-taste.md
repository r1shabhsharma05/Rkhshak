# Learn Taste — turn corrections into rules

Distilled from the learn-taste skill. Method in our own words; the full workflow lives in that source. Use when a session produced corrections — about design, code, wording, or process — that should survive into the next session instead of being re-learned.

## Hard rules
- Only the user's own corrections count. Never invent a rule the user did not state or approve.
- Every rule carries its why. A rule without a why is a superstition and will be misapplied.
- Nothing is written anywhere without approval. Propose; the user adopts.

## Workflow
1. **Collect corrections.** Gather every correction from the session: what was said, what was changed, what was rejected.
2. **Filter.** Drop one-offs, matters of taste with no general form, and anything the user already retracted. Keep only corrections that would change a future decision.
3. **Generalize and find the why.** Turn "change X to Y here" into "prefer Y over X when Z, because …". If the why is unclear, ask — do not guess it.
4. **Decide where it goes.** A project rule goes in the project docs or skill; a session rule goes in the report; a checkable rule becomes a lint check or a gate. The surface must match the rule's scope.
5. **Report and stop.** Present the proposed rules, the ones needing an answer, the conflicts with existing rules, and the skipped ones — then stop. Do not write anything until approved.
6. **Write on approval.** Only the approved rules, exactly as approved, in the agreed place.

## Required output format
- **Rules to add** — each with its why and its surface.
- **Needs your answer** — corrections whose why is unclear.
- **Conflicts** — a new rule that contradicts an existing one, with both stated.
- **Make it a check** — rules that can be enforced mechanically, named as checks.
- **Skipped** — corrections dropped, with the reason each was dropped.

## Invocation variants
- End of a session: harvest the whole session's corrections.
- Mid-session: harvest one thread's corrections when they keep recurring.
- Never silent: if no correction clears the filter, say so — "nothing worth keeping" is a result, not a failure.
