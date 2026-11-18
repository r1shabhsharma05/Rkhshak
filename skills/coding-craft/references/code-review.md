# Code Review — five axes, honest feedback, a loop that closes

Distilled from four sources, in our own words: code-review-and-quality (MIT), receiving-code-review (MIT), requesting-code-review (MIT), feedback-critic (MIT). Full method and examples live in those sources. Use before merging any change, when receiving review feedback, or when asking for review.

## The five-axis review
1. **Correctness.** Does it do what it claims? Are the edge cases handled? Do the tests prove the behaviour?
2. **Readability & simplicity.** Can a stranger follow it? Is there a simpler shape that does the same thing? (Size is governed by `minimal-code`; this axis is about clarity.)
3. **Architecture.** Does it respect module boundaries? Does it add a concept the codebase does not need? Does it duplicate something that exists?
4. **Security.** Untrusted input, secrets, auth, injection, exposure. A finding here blocks the merge regardless of the other axes. (Fixes go through `security-fix`.)
5. **Performance.** Is there a measured problem, or a speculative one? Never demand optimisation without a measurement; never ignore a measured regression.

## Review process
1. **Understand the context.** The change description, the issue, the intent — before the diff.
2. **Review the tests first.** Do the tests prove the claimed behaviour? A change whose tests do not prove it has not been reviewed, only read.
3. **Review the implementation.** Axis by axis, with a concrete case for every finding. No finding without an example.
4. **Categorize findings.** Blocking (must fix), suggestion (consider), question (clarify). A review with everything blocking is a review that was not prioritised.
5. **Verify the verification.** Did the author run the checks? Run them yourself where it matters — do not trust the report. See `references/verification.md`.

## Change sizing and descriptions
Small changes review better: one concern per change, atomic commits, a description that explains intent (why), not what the diff already shows. Dead code gets removed, not commented.

## Multi-model review pattern
A second reviewer — a different model or a fresh context — catches what the first missed, especially on security and correctness. Use it for high-risk changes; the second review is adversarial, not a rubber stamp.

## Handling disagreements
Disagree with a reason and a concrete case. If the evidence is genuinely ambiguous, say so and name what would settle it. Honesty in review means reporting uncertainty, not hiding behind confidence.

## Receiving review feedback
- **Response pattern:** acknowledge, verify the claim against the code, then act or push back with evidence. Never implement a suggestion blindly.
- **Forbidden responses:** dismissing without checking; implementing without understanding; arguing about tone instead of the finding.
- **Unclear feedback:** ask one precise question, quoting the feedback, before implementing. Guessing at intent wastes the review.
- **When to push back:** the feedback is technically wrong (prove it), out of scope for this change (say so, file it), or asks for speculative work (YAGNI — decline with the reason). If your pushback turns out wrong, correct it gracefully and say so.
- **From external reviewers:** address maintainer feedback promptly, on the same branch, in the same tone as the project.

## Requesting review
Ask when the work is complete and verified, not before. The request states: what changed, why, what was verified and how, what is uncertain, and what kind of feedback is wanted. A review request without verification is a request to do the author's job.

## The feedback loop (so mistakes stop repeating)
After every multi-step task, log the mistake: what went wrong, what the fix was, what rule would have prevented it. Distill the lesson into the standing rules. The log is reviewed, not just written — a lesson nobody re-reads is not a lesson. (See `codebase-intelligence` `references/learn-taste.md` for turning corrections into rules.)
