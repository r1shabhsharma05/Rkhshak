# Test Gate — the Verifier, production-style, after every step

A step is done when the Verifier says it is done — on fresh evidence,
against the real artefact. The builder's report is a claim; the
Verifier's run is the proof.

## Verifier independence (non-negotiable)
- The Verifier is a separate agent from the builder of the step. The
  agent that wrote the code never tests that code; the agent that cut
  the video never judges that cut.
- The Verifier re-runs the check itself. Reading the builder's report
  and agreeing is not verification.
- The Verifier's verdict is PASS or FAIL. There is no "mostly passes",
  no "passes except", no partial pass. A step with a known failure is
  a FAIL with the failure named.

## What "production-style" means
Test the way a big company tests a release — the real thing, used the
way a user would use it:

- **Build it fresh.** Run the real build command. A build that passed
  yesterday is not evidence today.
- **Run it fresh.** Start the real app / render the real video / open
  the real draft. Read the actual output.
- **Use it like a user.** Click through the flow, submit the form, play
  the video, read the post. A unit test passing does not prove the flow
  works.
- **Real behaviour, no mocks-as-proof.** A mock that stands in for the
  real service proves the mock works. If the real service cannot be
  reached, the step is BLOCKED with the reason — never passed on a mock.
- **Security and design gates apply at the final gate.** Before any
  deploy or launch: `security-audit`. Any UI: `design-unslop`. These
  are gates, not suggestions — a fail blocks the show step.

## The per-step gate
Before the next step starts, the Verifier posts:
```
STEP: <number>
CHECKS RUN: <each check — command or real behaviour — with its result>
VERDICT: PASS | FAIL
EVIDENCE: <command + output, or observed behaviour>
IF FAIL: <what failed, exactly, and what the owner should expect fixed>
```
- PASS → the Master marks the step done and dispatches the next step.
- FAIL → the step returns to its owner with the failing evidence.
  Fix loop capped at 5 rounds — see `execution-loop.md`.
- A step that cannot be tested (no test in the plan, no way to run it)
  is BLOCKED, not passed. The Master sends it back to the Planner.

## The final gate (before the show step)
After the last step passes, the Verifier runs the whole flow end to
end once more — the full user journey, not just the last step — and
posts a final gate report:
```
FINAL GATE: PASS | FAIL
FLOW CHECKED: <the full journey, step by step>
EVIDENCE: <what was run and observed>
OPEN: <anything still failing or untested, named honestly>
```
- Only a PASS final gate goes to the show step. A FAIL final gate
  returns the failing step(s) to their owners through the fix loop.
- The final gate report is part of what the Master shows the owner.
  The owner sees the evidence, not a summary of it.

## Evidence standard
- A check passes only on observed behaviour: a test command's output,
  a live probe, a rendered artefact, a played video.
- "Should pass", "looks right", "probably fine", and a previous run's
  output are not evidence. Fresh run, this turn, or it did not happen.
- Every verdict names the command or behaviour that proves it. A
  verdict without evidence is an opinion, and opinions do not pass gates.
