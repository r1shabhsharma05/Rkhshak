# Plan Format — human-readable, frozen once reviewed

The plan is the contract between the owner and the team. It must be
understandable at a glance: the owner reads it once and can explain it
back. If a step needs a second reading, rewrite the step.

## Template
```
GOAL: <one line — what "done" looks like, in the owner's words>
SCOPE: <in / out / undecided — copied from the research note>
BAR: <the best-in-market bar, one line>

STEP 1 — <plain name>              [owner: Coder]
  Do:    <one or two sentences, human tone, no jargon>
  Done:  <observable outcome — what the owner will see>
  Test:  <what the Verifier runs — command or real behaviour>
  Depends on: <step numbers, or "none">

STEP 2 — <plain name>              [owner: Editor] [P]
  ...

OPEN QUESTIONS: <anything still undecided, with who answers it>
```

## Rules for writing steps
- **One owner per step.** A step with two owners has no owner. If two
  roles must work on one outcome, split it into two steps.
- **Done-criteria are observable.** "Login works" is not observable;
  "a user signs in with email + code and lands on the dashboard" is.
  If the owner cannot see it, it is not a done-criteria.
- **Every step has a test.** The test names what the Verifier runs —
  a command, a real behaviour, a side-by-side check. A step with no
  test cannot enter the execution loop.
- **Steps in dependency order.** A step lists what it depends on. A
  step that depends on nothing can run first.
- **`[P]` marks parallel-safe steps only.** A step is `[P]` when it is
  independent: no shared file, no shared state, no dependency on
  another step in flight. Shared state means sequential — no exceptions.
  When in doubt, leave `[P]` off.
- **Human tone, human way.** Short sentences. No jargon without a
  plain-word translation next to it. No step longer than five lines.
- **No speculative steps.** Every step traces to the research note or
  the owner's words. "Might need it later" is not a step.

## Review, then freeze
1. Planner posts the plan to the board.
2. The team reviews once. Each role checks its own steps: is the
   done-criteria observable, is the test runnable, is the owner right?
   One round of fixes, then the plan is frozen.
3. **Frozen means frozen.** No silent edits to a step in flight. A
   change is a new step, added by the Master, with its own owner,
   done-criteria, and test — appended at the end, numbered, recorded
   on the board. History is never rewritten.
4. If the owner changes their mind mid-run ("change X"), that is a new
   step too — never a rework of a step already passed. Passed steps
   stay passed.

## What a bad plan looks like (reject it at review)
- A step with no owner, no done-criteria, or no test.
- A step that says "build the backend" with no observable outcome.
- `[P]` on two steps that touch the same file.
- A step the Verifier cannot test ("make it feel premium" with no
  checkable behaviour — rewrite it as observable, or drop it).
- Jargon the owner would not understand, with no plain translation.
