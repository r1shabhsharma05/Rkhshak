# Threat Model — STRIDE template (run before the audit)

Audit the design before you audit the code. A threat model names what can go wrong, so the audit checks the right things. Run this BEFORE the 85-check audit on a new project, and update it when the architecture changes.

## How to build it (STRIDE)
For each part of the system (frontend, API, database, storage, third-party services, mobile app), ask six questions:

| Threat | Question | Example |
|---|---|---|
| **S**poofing | Can someone pretend to be someone else? | Stolen token, weak password reset, no 2FA. |
| **T**ampering | Can someone change data they shouldn't? | Mass-assignment (`role` in request body), no ownership check, unsigned webhook. |
| **R**epudiation | Can someone deny doing something, with no record? | No audit logs for admin actions, payments, or permission changes. |
| **I**nformation disclosure | Can someone see data they shouldn't? | Missing RLS, IDs in URLs without ownership checks, verbose errors, secrets in logs. |
| **D**enial of service | Can someone make it unavailable or expensive? | No rate limits, no request-size limits, unbounded AI calls, no spending cap. |
| **E**levation of privilege | Can a normal user become an admin? | Self-promotion via signup, admin route without a server-side role check. |

## Template (copy, fill for the project)
```markdown
# Threat Model — <Product name> (<date>)

## System
- Components: <frontend, API, database, storage, third-party services, mobile app>
- Trust boundaries: <where untrusted input enters — every API route, every form, every webhook, every file upload>
- Assets: <what matters most — user data, payments, secrets, admin access>

## Threats (one row per threat)
| # | Component | STRIDE | Threat | Likelihood | Impact | Mitigation (85-check) | Status |
|---|---|---|---|---|---|---|---|
| 1 | API /auth/login | S | Brute-force login | High | High | Rate limits + lockout (6.1, 2.4) | Open / Mitigated |
| 2 | API /users/:id | T | User A edits user B's data | High | High | Ownership check on every route (3.1) | Open / Mitigated |

## Top risks (the 3–5 that matter most)
1. <threat> — <why it matters> — <mitigation>
```

## Rules
- **Data flows, not code.** Draw the data flow first (user → frontend → API → database → third-party). Threats live where data crosses a trust boundary.
- **Top risks first.** The audit prioritizes the top 3–5 risks. A threat model with 50 rows and no priorities is a list, not a model.
- **Update it.** When the architecture changes (new integration, new data, new role), update the threat model in the same change.
- **The threat model feeds the audit.** Each threat maps to an 85-check area. If a threat has no check, the audit is incomplete — add the check.
