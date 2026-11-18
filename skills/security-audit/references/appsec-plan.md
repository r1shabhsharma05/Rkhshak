# AppSec Plan — pick the right test per asset, one ranked plan

Use this when the request is "make my application secure" and the target is not yet a single URL or repo. The job is to pick the right test per asset, run it, and produce one ranked plan — not to run everything at maximum depth.

## 1. Map the assets

Ask (or read from the repo) and write the answers down before testing anything:

- **Source** — one repo, a monorepo, several services? Which languages and frameworks?
- **Running environments** — a staging deployment? A public production site? A local dev server only?
- **APIs** — REST, GraphQL, gRPC? Is there a machine-readable schema (OpenAPI, GraphQL introspection, `.proto`)?
- **Authentication** — can you get two test accounts in different tenants, plus a low-privilege and a high-privilege account? Most high-impact bugs need them.
- **Constraints** — out-of-scope paths, whether production may be touched, budget and time limits.

If there is no staging environment and production is off limits, say so early. A code-only review is still valuable, but it cannot prove exploitability against a live app.

## 2. Pick the right test per asset

| Asset | Test to run |
|---|---|
| Repository or working tree | White-box code review — see `pentest` skill, `references/code-pentest.md` |
| Live web app or staging site | Black-box web pentest — see `pentest` skill, `references/web-app-pentest.md` |
| REST / GraphQL / gRPC API | API pentest — see `pentest` skill, `references/api-pentest.md` |
| Assessment mapped to OWASP categories | OWASP coverage run — see `pentest` skill, `references/owasp-pentest-coverage.md` |
| Every pull request, continuously | Diff-scoped CI gate — see `pentest` skill, `references/ci-pentest-gate.md` |
| No local run possible, or an auditor-facing report is needed | Managed / continuous testing — see `pentest` skill, `references/managed-continuous.md` |

Sequence for a first assessment:

1. Review the code first. It is the cheapest run and it maps the authorization model.
2. Pentest staging with credentials, and pass the repo as a second target so the test keeps source context.
3. Add CI scanning, so later regressions are caught without another manual pass.

Run one asset at a time and read each report before starting the next. Findings from the code review make the live run sharper.

## 3. Consolidate into one plan

Findings arrive per run. Merge them into a single list and rank by **proven impact**, not by scanner severity:

1. Validated exploits reachable without authentication.
2. Validated cross-tenant or privilege-escalation issues.
3. Validated issues needing an authenticated account.
4. Unproven observations (configuration, dependency, and hardening notes) — flag as such, and never present them as confirmed vulnerabilities.

Deduplicate: the same root cause often surfaces in both the code review and the live pentest. Fix the root cause once.

## 4. Be honest about coverage

State plainly what was *not* tested — assets with no staging environment, categories a black-box run cannot reach (logging and alerting, supply-chain integrity, insecure design), and any run that hit its budget or turn cap before finishing. An empty result set from a truncated run is not a clean bill of health.

Then fix with the `security-fix` skill and re-test to prove each exploit is closed.

## How this maps to the 85 checks

Asset mapping and honest coverage feed the audit's scope step (workflow step 2) and the gate report. A plan that hides untested assets fails the evidence standard, even if every tested check passed.

## Provenance

Summarised in our own words from the application-security-testing workflow (Strix AppSec skill family, Apache-2.0) and the OWASP API Security Top 10 (2023).
