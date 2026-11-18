# Assess extension

For an idea you are unsure about — before any spec is written. Install from the project directory when needed (`specify extension add assess`). Five stages, in order: intake → research → define → shape → decide. Only survivors reach specify. **Killing an idea here is a success, not a failure** — that is the entire point of an assessment pipeline.

## Stage 1 — Intake

Capture the raw idea — however rough — and normalize it into a single intake note at `.specify/assessments/<slug>/intake.md`. Record what the idea is and where it came from, without judging it yet. List first-glance unknowns: the obvious questions that must be answered before anyone decides. Do not answer them here.

URL hygiene: record the sanitized URL (strip any userinfo and drop query/fragment parameters that may carry credentials or signatures — `token`, `sig`, `signature`, `key`, `password`, `access_token`, signed-URL schemes); keep scheme, host, and path. Never persist a verbatim URL that may embed secrets. Never issue a probe request to "see what it is" — the probe itself is the gated request. Fetch without prompting only from widely-used public sources; any other host needs explicit user confirmation first, and unrecognized hosts are refused.

## Stage 2 — Research

Gather the evidence needed to judge the idea honestly, at `.specify/assessments/<slug>/research.md`. This stage exists to **challenge** the idea as much as support it — prior art, real user signal, market context, data — so later stages rest on facts, not enthusiasm.

- Research **collects and cites evidence; it does not decide.** No verdict, no solution design.
- Cite sources. Mark invented entries `[NEEDS CLARIFICATION: …]`.
- If sources conflict, surface the discrepancy; do not silently pick one.

## Stage 3 — Define

Define the problem at `.specify/assessments/<slug>/problem.md`: who is affected, what hurts, goals, non-goals, and success metrics.

- Identify users (who experiences the problem) and stakeholders (who decides, funds, or is impacted).
- Set **goals** — the outcomes that would make solving this worthwhile.
- Set **non-goals** — what is explicitly out of scope, to bound the work and prevent creep.
- Establish a **baseline** — what happens if nothing is built (the cost of inaction). This is what decide weighs against.

## Stage 4 — Shape

Shape options from the problem, goals, non-goals, and evidence. Each option addresses the stated goals, respects the non-goals, and is grounded in evidence. Call out **rabbit holes** — the parts most likely to blow up scope — so decide sees them. Recommend one option with a short rationale tied to the problem's goals and metrics — or explicitly recommend **not proceeding** if no option clears the bar. Bound the concept: restate what is explicitly out of scope for the recommended option.

## Stage 5 — Decide

Render the verdict at `.specify/assessments/<slug>/decision.md`. Decide **judges; it does not spec or build.** It weighs the evidence already gathered and commits to a defensible call. `problem.md` must exist — you cannot decide on an undefined problem.

| Verdict | Meaning |
|---|---|
| **go** | The idea clears the bar. Hand it off to specify. |
| **needs-clarification** | Evidence is missing. Send it back to an earlier stage with the specific questions named. |
| **kill** | The idea does not clear the bar. Stop it with a documented reason. |

Record the verdict, the reasoning, and the evidence it rests on. A `go` hands the idea off to specify; a `kill` ends the pipeline with the reason on record.
