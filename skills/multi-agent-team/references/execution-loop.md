# Execution Loop — dispatch, do, report, verify, next

One step at a time, in plan order. The loop is the same for every step,
whether it is code, a video edit, a lead list, or a job application.

## The loop
```
1. Master dispatches the step   → brief on the board
2. Owner agent does the step    → works only inside the brief
3. Owner agent reports          → what changed + how verified + what is open
4. Verifier tests end-to-end    → PASS or FAIL with evidence
5. PASS → Master marks the step done, dispatches the next step
   FAIL → step returns to its owner with the failing evidence (fix loop)
```

## The brief (what the Master sends per step)
A brief is written, complete, and self-contained. The agent that
receives it should not need to ask a question to start.

```
STEP: <number + plain name>
OWNER: <role>
DO: <the step's "Do" from the plan, verbatim>
DONE WHEN: <the step's done-criteria, verbatim>
TEST: <the step's test — what the Verifier will run>
IN SCOPE: <files, accounts, channels this step may touch>
OUT OF SCOPE: <everything else — explicitly>
DEADLINE: <the step's place in the order; a wall-clock time only if the owner set one>
```

- **Write the brief to a file, never inline in a command string.**
  Briefs carry quotes and arbitrary text; inlining them is a bug.
- **In scope is a fence, not a suggestion.** Work outside the brief's
  scope is out of scope even if it looks useful. Useful-but-out-of-scope
  goes on the board as a proposed new step for the Master.
- **One brief, one agent, one step.** Never bundle two steps into one
  dispatch to save a round trip.

## The report (what the owner agent sends back)
```
STEP: <number>
CHANGED: <what was done, files / drafts / rows — concrete>
VERIFIED: <command run + output, or real behaviour observed>
OPEN: <what is still not done, and why — or "none">
```
- A report without a VERIFIED line is not a report. "Looks done" is
  not verification.
- The Master checks the report against the brief before the Verifier
  runs: did the change stay in scope, is the verification real? A
  report that fails this check goes back before testing starts.

## The fix loop — capped at 5 rounds
- A FAIL from the Verifier returns the step to its owner with the exact
  failing evidence: command, output, and what was expected.
- The owner fixes only the failing part, re-reports, and the Verifier
  re-tests. Each round is numbered on the ledger.
- **After 5 failed rounds, the Master stops the loop** and escalates to
  the owner with the failing evidence, the five attempts, and the
  options (narrow the step / accept the gap / kill the step). The team
  never retries silently past the cap.
- A fix that changes the plan is not a fix — it is a new step, and it
  goes through the Master.

## The ledger (kept by the Master, one line per step)
```
STEP 3 — Coder — DISPATCHED → DONE → PASS (Verifier, test output linked)
STEP 4 — Editor — DISPATCHED → DONE → FAIL round 1 → FIX round 1 → PASS
STEP 5 — Coder — BLOCKED — needs owner's answer on <question>
```
States: PENDING / DISPATCHED / DONE / PASS / FAIL (round N) / FIX
(round N) / BLOCKED / ESCALATED. The ledger is the truth about where
the run stands; if it is not on the ledger, it did not happen.

## Parallel steps
- Only `[P]` steps run in parallel, and only when they are independent
  — no shared file, no shared state, no dependency.
- Each parallel agent works in its own space and reports to the board,
  not to each other. Agents never coordinate directly; the Master
  integrates.
- If two parallel steps collide (same file, same state), the Master
  stops both, sequences them, and records the collision. A collision is
  a planning miss, not a worker error.
