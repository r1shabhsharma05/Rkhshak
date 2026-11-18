# Handoff Protocol — the shared board, and who talks to whom

All team communication runs through one shared board. There are no
side channels, no DMs between workers, and no worker-to-owner messages.
If it is not on the board, the team does not know it.

## The board
One written record per run, kept by the Master. Minimum contents:

1. **The command** — the owner's words, verbatim, plus any reference.
2. **The restatement** — goal + scope + done-criteria, one line.
3. **The research note** + gate verdicts per round.
4. **The frozen plan** + any appended new steps.
5. **The ledger** — one line per step (see `execution-loop.md`).
6. **Every report and verdict** — builder reports, Verifier verdicts
   with evidence, escalations.
7. **The final show** — result + test evidence + the owner's pass (or
   change request as a new step).

The board is append-only. Nothing is deleted, nothing is rewritten.
A correction is a new entry that names what it corrects.

## Message format (every board post)
```
FROM: <role>    TO: <role or "ALL">    STEP: <number or "—">
<one line: what this is>
<body: the content — report, verdict, question, evidence>
```
- One message, one subject. A report that is also a question is two
  messages.
- Evidence is attached, not described. A test result links or pastes
  the command + output; a claim without its evidence is an opinion.

## Who talks to whom
- **Owner ↔ Master only.** The Master is the single voice the owner
  hears and the single ear that hears the owner. Workers never message
  the owner directly — not to ask, not to show, not to apologise.
- **Worker → Master → worker.** Workers post to the board; the Master
  routes. Workers never coordinate directly with each other — the
  Master integrates, so a misunderstanding has one place to be caught.
- **Worker → owner need = escalation.** A worker that needs the owner
  posts `ESCALATE` to the Master with the exact question. The Master
  asks the owner once, in one message, with the context attached —
  never a bare question, never a chain of follow-ups.

## Intake — the one-line restatement
Before any research starts, the Master posts:
```
GOAL: <what done looks like> | SCOPE: <in / out> | DONE WHEN: <observable outcome>
```
- If the command is ambiguous, the Master asks the owner **once**,
  with the options named, and waits. Never guess. A guessed scope is
  a wasted run.
- If the command bundles several independently testable capabilities
  (e.g. a website + a video + a job search), the Master splits it into
  one run per capability, in the order the owner confirms — see
  `spec-kit` capability mapping. One run, one goal.

## Escalation — when the Master stops and asks
- Research gate fails round 2.
- Fix loop hits 5 rounds.
- A worker is blocked on something only the owner can answer or
  provide (a password, a one-time code, a decision, an account).
- Two worker results contradict each other beyond the brief.
- The plan must change structurally mid-run.
- The budget (time, cost, or rounds) runs out.

An escalation names: what happened, the evidence, what was already
tried, and the options with the Master's recommendation. It never
names only the problem. The owner decides; the decision is recorded
on the board, and the run continues from it.
