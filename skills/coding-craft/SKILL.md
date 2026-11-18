---
name: coding-craft
description: "Write, test, debug, review, and verify code properly — test-first development, systematic debugging, five-axis review, verification before any claim of done, clean APIs, and honest docs. Use when implementing any logic, fixing any bug, reviewing a change, designing or integrating an API, simplifying code, or documenting a decision."
---

# Coding Craft — write it right, prove it works

## Purpose
Code that is not tested is a guess; a fix that is not verified is a hope; a review that is not structured is a vibe. This skill is the working discipline for writing code: test first, debug by root cause, review on five axes, verify before claiming done, design APIs that survive contact with users, and document the decisions that matter.

Use it when implementing logic, fixing a bug, reviewing a change (yours or anyone's), designing or integrating an API, simplifying code, removing a deprecated system, measuring performance, adding telemetry, testing in a browser, or writing docs and decision records.

## How it works (any user, any project, any stack)
No setup. No config. The agent reads this skill and the references, then writes code by the rules below. It composes with `minimal-code` (smallest complete change — the size rule) and `code-humanizer` (human voice — the style rule): this skill is the correctness rule.

## Workflow
1. **Test first.** Discover the repo's test commands, then red-green-refactor — see `references/tdd.md`.
2. **Debug by root cause.** Reproduce, localize, reduce, fix the cause, guard, verify end-to-end — see `references/debugging.md`.
3. **Review on five axes.** Correctness, readability, architecture, security, performance — then handle the feedback properly — see `references/code-review.md`.
4. **Verify before claiming done.** Run the checks fresh, read the output, claim only what the output proves — see `references/verification.md`.
5. **Simplify without changing behaviour.** Preserve behaviour exactly, follow project conventions — see `references/simplification.md`.
6. **Design the boundary.** Contract-first APIs, validated at the boundary, resilient integrations — see `references/api-design.md` and `references/api-integration.md`.
7. **Mind the long tail.** Dependencies, deprecation, performance, observability — see `references/dependencies.md`, `references/performance.md`, `references/observability.md`.
8. **Test where it runs.** Browser tests with real tooling — see `references/testing-in-browser.md`.
9. **Write it down.** ADRs, comments, READMEs, changelogs — and check the draft reads — see `references/docs-and-decisions.md`. Platform specifics live in `references/platform-notes.md`.

## References
| File | What it covers |
|---|---|
| `references/tdd.md` | Red-green-refactor, prove-it bug pattern, test pyramid, good-test rules |
| `references/debugging.md` | Stop-the-line, reproduce → localize → reduce → fix → guard → verify, three-fix rule |
| `references/code-review.md` | Five-axis review, review process, receiving and requesting review, feedback loop |
| `references/verification.md` | Iron law — run it fresh, read the output, claim only what it proves |
| `references/simplification.md` | Simplify without changing behaviour — principles, process, language notes |
| `references/api-design.md` | Contract-first API and interface design — REST, types, idempotency |
| `references/api-integration.md` | Resilient third-party integration + Zod validation at boundaries |
| `references/dependencies.md` | Dependency diagnosis, deprecation, and migration patterns |
| `references/performance.md` | Measure → bottleneck → fix → verify → guard, with targets |
| `references/observability.md` | Define working, signals, logs, metrics, traces, alerts, runbooks |
| `references/testing-in-browser.md` | Playwright patterns + DevTools debugging workflow |
| `references/docs-and-decisions.md` | ADRs, comments, API docs, README, changelog, first-reader check, teach-back |
| `references/platform-notes.md` | Mobile-native feel, Swift, typed AI integration |

## Rules
- **No test, no done.** New logic ships with a test; a bug fix ships with a regression test that failed first.
- **Root cause, not symptom.** A fix that does not name the cause is a patch; it will be back.
- **Never trust a report — verify it.** A claim of "fixed" or "passing" is worthless until the check ran fresh and its output was read.
- **Review the tests first.** A change whose tests do not prove the behaviour has not been reviewed, only read.
- **Smallest complete change.** `minimal-code` governs size; this skill governs correctness. Both apply.
- **Evidence, not claims.** A check passes only on observed output — test runs, build logs, live probes.

## Provenance
Distilled in our own words from: test-driven-development (MIT), debugging-and-error-recovery (MIT), code-review-and-quality (MIT), receiving-code-review (MIT), requesting-code-review (MIT), feedback-critic (MIT), verification-before-completion (MIT), code-simplification (MIT), api-and-interface-design (MIT), codebase-design, api-integration-specialist (MIT), zod-pro (MIT), dependency-doctor (MIT), deprecation-and-migration (MIT), performance-optimization (MIT), observability-and-instrumentation (MIT), playwright-pro (MIT), browser-testing-with-devtools (MIT), documentation-and-adrs (MIT), first-reader (MIT), teach (MIT), mobile-native, write-swift (BSD/MIT), typesafe-ai (MIT). Full method and examples live in those sources.
