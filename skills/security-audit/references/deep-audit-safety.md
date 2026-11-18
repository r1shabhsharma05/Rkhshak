# Deep-Audit Safety — sandboxed execution, coverage ledger, prior runs

This file carries the safety and coverage discipline missing from the short Cloudflare summary in `references/cloudflare-audit.md`. Use it whenever a full / comprehensive / end-to-end review runs (full audit mode). In guidance mode (answering a question, a focused review), the sandbox rules still apply to any code you execute.

Source: summarised in our own words from the Cloudflare `security-audit-skill` (MIT, 2025–2026), https://github.com/cloudflare/security-audit-skill. The upstream repo holds the full reconnaissance, hunting, validation, and reporting guides.

## Sandboxed execution (applies in both modes)

Source inspection is read-only. Run target-controlled builds, tests, processes, browsers, emulators, fuzzers, and fixture processing only inside an OS-enforced sandbox that provides all of these controls:

- No external network.
- An empty environment — record only the allowlisted variable *names* plus safe non-secret values needed to reproduce a check. Never capture the ambient environment, inherited variables, credential values, or authentication state.
- Read-only target source; writes only to an agent-owned scratch directory, never to `/tmp`, the host home directory, or another agent's directory.
- CPU, memory, and time limits.

If a control cannot be enforced, do not execute target code — report the missing capability as a needs-validation blocker.

Every reproduced check records the command, the exact test input, the sandbox limits, and only the allowlisted environment variable names. Stop at the minimum effect that proves the boundary result (a wrong return value, an unauthorized dummy record, a sanitizer finding, a policy difference). Do not extend a local check into persistence, post-fault, or concealment material.

## Coverage ledger (full audit mode)

No one pass is complete. Build a deterministic coverage plan before hunting and update it after every result:

- Coverage units are stable: surface × trust boundary × attack class.
- The parent agent alone updates the ledger. Hunters work from ledger assignments, one unit each, and return structured candidates — never prose-only results that cannot be deduplicated or verified.
- A scoped or quick run seeds ledger units only for in-scope surfaces and records everything else as `out_of_scope` — never as `covered`. A partial run must present itself as partial coverage.

## Prior runs

If prior runs exist, read every compatible coverage ledger and findings file before planning the current run:

1. Compare the relevant current source with each prior record. A prior source ref alone is not evidence that a path is unchanged.
2. Carry a prior `confirmed` record forward only when its relevant source and conditions are unchanged and its evidence still meets the current bar — and send it through the current verification path.
3. When relevant source changed, create a current revalidation unit. The record stays confirmed only if current independent validation establishes it.
4. Prior `needs_validation`, `deferred`, `blocked`, and `out_of_scope` records are current work. They never suppress a current unit.
5. A prior `rejected` record suppresses only the unchanged failed claim, not coverage of its unit.

## Budget gate (full audit mode)

A coverage unit is roughly one hunter assignment; one surviving candidate is one or two verifier assignments. When the user sets a budget (maximum agent invocations), record it before launching anything and reserve critics and validation **before** hunting. If the budget cannot fund reconnaissance plus one critic plus at least one verifier, launch nothing: ask for a larger budget, narrower scope, or a coarser profile. If the remaining budget cannot validate every candidate, stop hunting, validate in fingerprint order while the budget permits, mark the run incomplete with its exact reason, and disclose the gap in the report. Never exceed a user-set strict budget silently.

## Profiles (full audit mode)

- **`quick`** — a bounded pass for small targets, re-runs, or a fast first look. One hunter wave, one critic pass, one fresh verifier per candidate.
- **`standard`** — the workflow as written (see `references/cloudflare-audit.md`).
- **`deep`** — high-stakes or large targets. Split ledger units per subsystem, run critic waves to a clean pass, keep candidate validation and final record verification as separate fresh agents.

Profiles change breadth and redundancy, never the evidence bar. They never scale away the candidate gate, the source/local execution boundary, needs-validation discipline, or independent verification.

## Terminal states

End only in one of two states: (a) all final artifacts are written and both validators pass, or (b) the run is recorded `incomplete` with its exact reason and the gap is disclosed in the report. Never stop mid-phase.
