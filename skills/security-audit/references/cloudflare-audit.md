# Cloudflare Security Audit — 6-Phase Workflow (summary)

Source: Cloudflare's `security-audit-skill` (MIT License, Copyright 2025–2026 Cloudflare, Inc.), https://github.com/cloudflare/security-audit-skill. This file is a compact summary for use inside Rkhshak. For the full skill (reconnaissance, hunting, validation, and reporting guides), read the upstream repo.

## Modes
- **Guidance mode (default):** answer security questions, do focused reviews, triage a finding. Do NOT run all six phases, create output directories, or write audit artifacts.
- **Full audit mode:** run only when the user explicitly asks to audit or pen-test a codebase, asks for a full/comprehensive/end-to-end review, or requests report artifacts. Run all six phases.

## The six phases (full audit mode only)
1. **Reconnaissance** — map the source, trust boundaries, local build paths, and a deterministic coverage ledger. Read prior runs first.
2. **Coverage-led hunting waves** — isolated hunters work from the ledger, one assignment per coverage unit, and return structured candidates.
3. **Candidate validation** — consolidate fingerprints; give every candidate to a fresh source verifier.
4. **Structured output** — write `findings.json` (confirmed / needs_validation / rejected), validate it against the schema, and validate the coverage claim.
5. **Independent record verification** — fresh agents verify final source claims and reconcile corrections.
6. **Target-neutral report** — derive `REPORT.md`, `FINDINGS-DETAIL.md`, and `NEEDS-VALIDATION.md` from the final records.

End only in one of two terminal states: (a) all Phase 6 artifacts written and both validators pass, or (b) `run_status: "incomplete"` recorded with its exact reason and the gap disclosed in the report. Never stop mid-phase.

## Core principles
- **Require a boundary and result.** Every candidate names the lower-trust principal, the intended control, the crossed boundary, the affected principal/resource, and a concrete observed result. A missing best practice with no reachable boundary violation is not a finding.
- **Use bounded local evidence.** Static analysis establishes the source path. Sandboxed local tests resolve behaviour. Stop at the minimum effect. Never probe deployed endpoints, live services, production identities, or other users' data.
- **Respect source visibility.** If a control (proxy, provider, browser header, identity policy) is required but absent from the repo, do not assume presence or absence — mark it `needs_validation` with the exact missing fact.
- **Separate priority from certainty.** Only `confirmed` records get severity. `needs_validation` has no severity.
- **Smallest effective fix.** Identify the invariant the code must enforce and the narrowest source change that enforces it at the last trusted decision point. The audit describes fixes; it does not modify target source.

## Severity anchors
- **critical** — unauthenticated actor gains code execution, full data-store access, or takeover of arbitrary accounts.
- **high** — an actor fully defeats an explicit security control with real consequences (auth bypass, cross-tenant read/write, stored script execution, authenticated code execution, unauthenticated remote stop of a shared service).
- **medium** — a real boundary violation with limited blast radius or uncommon preconditions.
- **low** — disclosure of non-secret internals, or an effect requiring sustained effort for minimal gain.
- **informational** — a confirmed but minimal-impact observation.

## Anti-patterns (never do these)
1. Checklist deviations presented as vulnerabilities.
2. Defense-in-depth advice with no reachable boundary violation.
3. Live or shared-environment testing where bounded local evidence is insufficient.
4. Guessing provider, proxy, browser, identity, or deployment behaviour not present in source.
5. Treating intended same-principal authority or self-impact as a cross-boundary result.
6. Reporting a parser or runtime effect stronger than the observed effect.
7. Emitting prose-only hunter results that cannot be deduplicated or verified.
8. Re-reporting carried same-source prior confirmed records.
9. Assigning severity to `needs_validation` records.
10. Writing the report before independent verification or letting prose and JSON disagree.

## How it fits Rkhshak
- Use the 85-check audit (`pre-launch-audit-85-rules.md`) as the checklist. Use this Cloudflare workflow as the deep-audit method when the user asks for a full, comprehensive, or end-to-end review — it adds coverage-led hunting, candidate validation, and independent verification on top of the checklist.
- The Rkhshak multi-agent roles (Auditor / Fixer / Verifier) map to the Cloudflare roles (hunters / verifiers / parent). Preserve the independence boundaries: the agent that finds a candidate never validates it, and the agent that fixes never verifies its own fix.
