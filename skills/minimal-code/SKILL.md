---
name: minimal-code
description: "Write the least code that solves the problem - delete first, use the library, no dead code, no speculation."
---

# Minimal Code

## Purpose
Most code is too much code. Extra lines are not free — every line is something to read, to test, to break, and to maintain. This skill makes code small: the least code that solves the problem completely, nothing more.

Use it when writing new code, and when shrinking existing code. The result is fewer lines, fewer bugs, and code a human can hold in their head.

## When to use it
- Writing any new feature, fix, or change.
- Reviewing a change that feels too big.
- Cleaning up a file that grew past what it needs.
- Any time the question is "can this be smaller?"

## How it works (any user, any project, any stack)
No setup. No config. The agent reads this skill and the references, then writes or shrinks code by the rules below.

## Multi-agent
Works with Claude, Codex, and any agent that reads SKILL.md. The rules are written as plain checks, not model-specific tricks.

## Workflow
1. **Understand the task.** What is the smallest change that solves it completely? Say it in one sentence before writing any code. List every place the change must reach: callers, tests, fixtures, config, exports.
2. **Run the decision ladder** (see `references/ponytail.md` — the ponytail method, merged here). Take the first option that fully works: (1) does it need to exist? (2) already in this codebase? (3) stdlib/platform feature? (4) an installed dependency? (5) one line a reader gets at a glance? (6) otherwise, the minimum code that works.
3. **Delete first.** Before adding anything, remove what the change makes unnecessary (see `references/delete-first.md`). A change that deletes more than it adds is a good change.
4. **Write the smallest complete change.** One job, one place, no speculation. If the task doesn't ask for it, don't build it. Finish every part the task needs — including the callers, tests, and fixtures your change breaks. A shortcut with a known limit gets a `shortcut: <the limit>, <when to upgrade>` comment.
5. **Shrink what you wrote.** Re-read the change. Remove the duplicate, the wrapper, the one-use helper, the defensive check that can't happen. If a line doesn't earn its place, delete it.
6. **Verify.** Run the checks in `references/measure.md`: tests pass, no dead code, the diff is as small as it can be. Report the diff size (lines added vs lines removed). End with one or two lines: what you skipped or did not check, and any risk the user must know.
7. **Judge abstractions.** Before abstracting, run `references/abstraction-judgment.md` (AHA): rule of three, same reason to change, clear name, no flag-soup. If the abstraction isn't earned yet, leave the duplication.
8. **YAGNI.** Before adding anything, run `references/yagni.md`: is there a requirement, a user, or a test that needs this today? If not, don't build it. No config for one value, no future-proof frameworks, no dead code kept "in case".
9. **Dependency diet.** Before adding a dependency, run `references/dependency-minimalism.md`: count them, make it earn its place, one per job, small + maintained, remove what you don't use.
10. **Config diet.** Before adding an option, run `references/config-minimalism.md`: sane defaults first, no config for one value, every option has a user, config in one place.
11. **API diet.** Before adding an endpoint, run `references/api-surface-minimalism.md`: fewest endpoints, fewest params, no speculative endpoints, one shape per resource.

## References
| File | What it covers |
|---|---|
| `references/delete-first.md` | What to delete (dead code, commented code, speculation, one-use wrappers) + how to delete safely |
| `references/smallest-change.md` | The smallest complete change — one sentence, library first, when minimal is wrong |
| `references/measure.md` | Prove it — diff size, files touched, new concepts, dead code, pre-ship checks |
| `references/ponytail.md` | The ponytail method merged — decision ladder, shortcut comments, never-cut list, levels, review/audit/debt modes |
| `references/abstraction-judgment.md` | AHA — when NOT to abstract: rule of three, same reason to change, clear name, no flag-soup |
| `references/yagni.md` | You Aren't Gonna Need It — build only what today needs: no speculative features, no config for one value, no dead code |
| `references/dependency-minimalism.md` | The dependency diet — count them, make each earn its place, one per job, small + maintained, remove unused |
| `references/config-minimalism.md` | Config diet — sane defaults, no config for one value, every option has a user, config in one place |
| `references/api-surface-minimalism.md` | API surface diet — fewest endpoints, fewest params, no speculative endpoints, one shape per resource |

## Levels
| Level | Behavior |
|---|---|
| **lite** | Build what was asked. Name the smaller option in one line and let the user pick. |
| **full** | The rules above. Default. |
| **ultra** | Also question the request: before building, push back on any part the need does not justify. |

## Modes (see `references/ponytail.md`)
- **Review** — review a diff/PR like the senior dev who will be paged when it breaks (correct, safe, holds under load, tested, fast, lean). Every finding needs a concrete case.
- **Audit** — same checks on the whole repo, most important first. Map first, trace the main flows, end with a ranked list and "fix this first".
- **Debt ledger** — harvest every `shortcut:` comment into one ledger; flag markers with no upgrade trigger.

## Rules
- **Delete before adding.** The first question is always "what can I remove?"
- **No speculative features.** If the task doesn't ask for it, it doesn't get built. "Might need it later" is not a reason.
- **No dead code.** Unused functions, unreachable branches, commented-out code, leftover experiments — all deleted, not commented.
- **Library first.** A hand-built version of something the library does is a bug waiting to happen.
- **Smallest complete change.** "Complete" matters as much as "smallest" — the change must fully solve the task, with tests, not half of it.
- **Readability beats brevity.** Minimal is not golf. If removing a line makes the code harder to read, keep the line. A clear name is worth a line. A comment that explains WHY is worth a line.
- **One change, one diff.** A change does one thing. If it does two things, split it.
