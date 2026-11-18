# Analyze

A non-destructive cross-artifact consistency and quality analysis across `spec.md`, `plan.md`, and `tasks.md` — run only after tasks generation has produced a complete `tasks.md`. When `data-model.md` exists, also check constrained-field task citations and constraint consistency against it.

## Operating constraints

- **Strictly read-only.** Do not modify any file. Output a structured analysis report. Offer an optional remediation plan — the user must explicitly approve before any follow-up editing happens.
- **Constitution authority is non-negotiable.** A constitution conflict is automatically CRITICAL and requires adjusting the spec, plan, or tasks — never diluting, reinterpreting, or silently ignoring the principle. If a principle itself needs changing, that happens in a separate, explicit constitution update outside analyze.
- **Focus on high-signal findings. Limit to 50 findings total;** aggregate the remainder in an overflow summary.

## What to check

Load only the minimal necessary context from each artifact:

- **From spec:** overview/context, functional requirements, success criteria, user stories, edge cases.
- **From plan:** technical context, constitution check, research decisions, data model, contracts, quickstart scenarios.
- **From tasks:** task list, phase structure, dependencies, `[P]` markers, story labels, data-model citations.

Check for: **duplication** (same requirement stated twice, in different words), **contradiction** (spec says X, plan says not-X; task constraints contradicting the data model), **ambiguity** (unquantified adjectives, untestable acceptance criteria), **coverage gaps** (a requirement with zero tasks, a user story with no tests where tests were requested, a constrained field with no resolving citation), **terminology drift** (same concept under different names), **missing non-functional coverage** (security/performance requirements with no tasks), **underspecified edge cases**.

## Severity

| Severity | Meaning |
|---|---|
| **CRITICAL** | Violates a constitution MUST, missing core spec artifact, or a requirement with zero coverage that blocks baseline functionality. |
| **HIGH** | Duplicate or conflicting requirement, ambiguous security/performance attribute, untestable acceptance criterion, missing/unresolved constrained-field citation, contradictory task constraints. |
| **MEDIUM** | Terminology drift, missing non-functional task coverage, underspecified edge case. |
| **LOW** | Style/wording improvements, minor redundancy not affecting execution order. |

## Report format

A Markdown report (no file writes):

| ID | Category | Severity | Location(s) | Summary | Recommendation |
|----|----------|----------|-------------|---------|----------------|
| A1 | Duplication | HIGH | spec.md:L120-134 | Two similar requirements … | Merge phrasing; keep clearer version |

One row per finding, stable IDs prefixed by category initial. End with the remediation plan (only as a proposal) and the counts by severity.
