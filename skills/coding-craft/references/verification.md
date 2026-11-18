# Verification Before Completion — the iron law

Distilled from the verification-before-completion skill (MIT). Method in our own words; the full gate lives in that source. Use when about to claim work is complete, fixed, or passing — before committing, before creating a PR, before reporting done.

## The iron law
A claim of "complete", "fixed", or "passing" is made only after the verification command ran fresh and its output was read. No exceptions for "it obviously works", "I just changed one line", or "the other agent said so".

## The gate function
1. **Run the check fresh.** The real command, in the real environment, right now — not from memory, not from an earlier run, not from a report.
2. **Read the output.** All of it, not the summary line. A passing summary with a failing detail is a failure.
3. **Claim only what the output proves.** Quote the command and the relevant output with the claim. "Tests pass" means the test command ran and reported pass; nothing else.
4. **State the actual status.** If the check fails, the status is "fails", with the error — never a softened version.

## Common failures
- Trusting another agent's report ("fixed, all tests pass") without verifying independently — the report is a claim, not evidence.
- Accepting "linter passed" as proof the build succeeds. A linter is not a compiler; a type check is not a runtime test.
- Running the check on the wrong code (stale build, wrong branch, cached output) and claiming the result for the new code.
- Reading the code and concluding it works, instead of running it.

## Red flags — stop
- About to claim done without having run anything in this session.
- About to commit or open a PR on the strength of someone else's word.
- A verification step was skipped "because it is slow". Slow is not skipped; slow is run once, properly.

## Rationalization prevention
Every rationalization has the same answer: run it. "It is a trivial change" — run it. "I already verified the same thing" — that was the old code. "The CI will catch it" — CI is the backstop, not the verification.
