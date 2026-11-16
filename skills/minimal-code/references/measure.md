# Measure — prove the change is minimal

Minimal is a claim. Measure it, don't assert it.

## The numbers
- **Diff size.** Lines added vs lines removed. Report both. A good change often removes more than it adds.
- **Files touched.** The fewest files the task needs. If the change touches 10 files for a one-sentence task, something is wrong.
- **New concepts.** New functions, new types, new config, new dependencies. Each one is a cost. Zero new concepts is ideal; one is fine; three needs a reason.
- **Dead code.** After the change, search for unused functions, imports, and branches. The count must be zero (or the leftovers named with a reason).

## The checks (run before shipping)
- [ ] Tests pass (all of them, not just the new ones).
- [ ] The diff does one thing (the one-sentence change). Nothing else snuck in.
- [ ] No dead code added. No dead code left behind that this change made dead.
- [ ] No speculative code (nothing built for a use case nobody asked for).
- [ ] No hand-built version of something the library does.
- [ ] No commented-out code.
- [ ] The change is readable in 30 seconds by someone who didn't write it.

## How to report it
After every change, report:
- **Outcome:** what the change does (one sentence).
- **Diff:** files touched, lines added, lines removed.
- **Evidence:** test results, and the checks above (all passed, or which failed and why).

## When the numbers look bad
- Diff is huge for a small task → split the change.
- More lines added than removed, and nothing was deleted → ask "what can I remove?"
- New dependency added → ask "does the library/framework already do this?"
- New concept (type, config, helper) → ask "is there an existing concept that already covers this?"
