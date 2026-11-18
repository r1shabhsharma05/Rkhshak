# Adversarial Review — doubt the decision before it stands

Distilled from two sources, in our own words: doubt-driven-development (MIT) and elephant-goldfish-model (Apache 2.0, google/elephant-goldfish-model). Full procedures live in those sources. Use when a non-trivial decision must be cross-examined before proceeding, or when a design document needs a spec-first review.

## Doubt-driven review (for decisions)
1. **CLAIM — surface what stands.** Write down the decision and what it claims, in the smallest reviewable form.
2. **EXTRACT — smallest reviewable unit.** Pull out the artifact (the code, the design, the plan) and the contract it must satisfy (the requirements, the constraints). The reviewer gets both and nothing else — no persuasion, no context that argues for the decision.
3. **DOUBT — invoke the fresh-context reviewer.** A reviewer with no prior context reads the artifact against the contract and attacks it: what is wrong, what is assumed, what is unproven. Escalate across models for high-stakes decisions (a second model, read-only, given the same artifact and contract via a file, never via shell interpolation).
4. **RECONCILE — fold findings back.** Each finding gets one outcome: fix it, contest it with evidence, or decline it with a reason. No finding is silently dropped.
5. **STOP — bounded loop, not recursion.** The review runs a bounded number of rounds. When the rounds are spent, the decision stands or falls on the evidence — no infinite re-review.

## Elephant–Goldfish review (for design documents)
- **The elephant** remembers everything: the full design, the standards, the history. It drafts and holds the long view.
- **The goldfish** remembers nothing: each review round gets a fresh context — the target document and its standard, nothing else. Fresh eyes catch what familiarity hides.
- **Freshness is fail-closed.** A reviewer counts as fresh only when every freshness condition holds (no prior turns on this design, no memory of earlier rounds, only the target files). If freshness cannot be proven, the round does not count.
- **The pipeline:** brainstorm the idea → draft against the document standards → review in fresh-context rounds → resolve each finding (contest, escalate, propose fix, or decline) → drift report (did the design drift from its own standards?).
- **Reviewer personas:** read the persona briefs before spawning a reviewer; one persona mandate per brief, pasted verbatim. A reviewer without a mandate reviews nothing in particular.
- **Standing rules:** every artifact is written to a file with its path given; never dump a long document in chat. **Known limits:** freshness is instruction-enforced, not sandboxed — a reviewer sharing the filesystem can disobey the forbidden-files rule. State this plainly; never claim full isolation.

## When to use which
- Doubt-driven for a decision or a change: small, fast, adversarial.
- Elephant–Goldfish for a design document: slower, structured, standards-checked.
- Both are bounded. A review that never ends is a decision that never ships.
