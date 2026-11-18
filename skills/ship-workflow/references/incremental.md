# Incremental Implementation — thin slices, honest scope

Distilled from two sources, in our own words: incremental-implementation (MIT) and scope-creep-detector (MIT) with its `scope-signals.md`. Full method lives in those sources. Use when implementing any feature that touches more than one file, or when picking up the next task from a plan.

## The increment cycle
One thin, verifiable slice at a time: implement → verify → commit (or checkpoint) → next slice. A slice is complete when it is demonstrated working, not when its code is written. Never carry an unverified slice into the next one.

## Slicing strategies
- **Vertical slices (preferred).** A thin end-to-end piece of value, through every layer it touches. Demonstrable at every step.
- **Contract-first slicing.** Define the interface between the slices first, then build each side against the contract.
- **Risk-first slicing.** Build the riskiest, most uncertain part first — if it cannot work, everything else is wasted.

## Implementation rules
- **Rule 0: simplicity first.** The simplest slice that demonstrates the value.
- **Rule 0.5: scope discipline.** The slice contains only what its task names. Anything else is a new task or a scope question.
- **Rule 1: one thing at a time.** One slice, one concern.
- **Rule 2: keep it compilable.** The tree builds and the tests pass after every slice. A red tree is a stopped line.
- **Rule 3: feature flags for incomplete features.** An unfinished feature hides behind a flag; it never ships half-visible.
- **Rule 4: safe defaults.** The default behaviour is the old behaviour until the new one is proven.
- **Rule 5: rollback-friendly.** Every slice can be reverted on its own.

## Increment checklist
Each slice: demonstrated working, tests green, diff reviewed, committed or checkpointed, next slice named. A slice missing any item is not done.

## Scope-creep detection (on every diff)
Establish the intent first: what the task said, in one sentence. Then classify the diff against it:
- **In scope:** the change the task asked for, including its tests and its direct consequences.
- **Related but separate:** a real improvement that belongs in its own task — split it out, do not smuggle it in.
- **Unrelated:** a change with no connection to the intent — remove it.
- **Broad:** the diff touches far more than the task needs — the task was too big, or the change wandered.
- **Dependency addition:** a new dependency needs its own justification (see `minimal-code` dependency diet).
Recommend keep, split, or justify for each item, and write the scope report: what was kept, what was split, what was justified and why. A justification is a reason with evidence, not a feeling.
