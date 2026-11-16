# Validation Gate — accept only strict improvement

The gate is the whole point. Without it, "training" is just rewriting the skill until it feels better. With it, every accepted change is proven better on data the skill never trained on.

## The rules
- **Held-out validation split.** Train, validation, and test are three disjoint sets. The skill trains on train, is gated on validation, and is finally scored on test. Never mix them.
- **Strict improvement only.** A candidate ships only if its validation score is strictly higher than the current best. Equal is not improvement — equal is rejected. A tie means the edit added nothing.
- **Rejected-edit buffer.** Rejected edits are kept, not deleted. A rejected edit that keeps reappearing across epochs is a signal (the optimizer thinks it matters, the gate disagrees) — read the buffer before the next epoch, don't just retry the same edit.
- **No-regression mode.** When enabled, every validation task must preserve or improve its score — one task getting worse blocks the whole candidate, even if the average went up. Use it when a single regression is unacceptable (safety, correctness, money).
- **Missing or non-finite score blocks the candidate.** If a validation task has no result, or its score isn't a number, the candidate is blocked. A missing measurement is not a pass.
- **Split leakage kills certification.** Once a task has entered training, it can never move into validation or test. Validation exposure likewise prevents later claims of pristine test coverage. If no disjoint validation pool remains, the gate reports leakage and does not certify the edits — the run is void, not "probably fine".
- **Gate stays on by default.** Turning the gate off is allowed only for a diagnostic run (to see what the optimizer would do ungated). Ungated results are never shipped and never reported as improvements.

## What the gate is NOT
- Not a vibe check. The gate is a number on a held-out split, not "it looks better".
- Not the test split. Gating on test is cheating — it turns test into validation and leaves you with no honest final number.
- Not optional for small changes. One-line edits go through the same gate. A small edit can break as much as a big one.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Train / validation / test splits are disjoint | A task appearing in two splits |
| 2 | Candidate accepted only on strict validation improvement | An equal-or-worse candidate shipped |
| 3 | Rejected edits kept in a buffer, reviewed before next epoch | Rejected edits deleted or blindly retried |
| 4 | No-regression mode used where a single regression is unacceptable | An average gain hiding a task that got worse |
| 5 | Missing / non-finite scores block the candidate | A missing measurement counted as a pass |
| 6 | No split leakage (training tasks never enter validation/test) | Gate certifying edits after leakage |
| 7 | Gate on for every shipped change | An ungated change reported as an improvement |
