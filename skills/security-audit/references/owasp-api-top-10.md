# OWASP API Security Top 10 (2023) — mapped to the 85 checks

The 85-check audit covers API abuse (Area 6), but not the full API-specific risk list. Run these 10 checks on every API. Each maps to an 85-check area — if the 85-check area passes, this item passes; if it fails, the 85-check finding is the one to report.

| # | Risk | What to check | 85-check |
|---|---|---|---|
| API1 | Broken Object Level Authorization (BOLA) | Every object access checks ownership (not just "is logged in"). Try accessing another user's object by ID — it must fail. | 3.1 |
| API2 | Broken Authentication | Auth is strong and consistent: tokens verified with signature, sessions expire, no default secrets, rate limits on login/OTP. | 2.1–2.7, 6.1 |
| API3 | Broken Object Property Level Authorization | Mass-assignment is blocked: the request body can't set `role`, `is_admin`, `plan`, `credits`, `balance`, `verified`. Only allowed fields are writable. | 3.2 |
| API4 | Unrestricted Resource Consumption | Limits on request size, pagination (max page size), file upload size, AI/compute calls, and expensive queries. No endpoint lets one user burn the budget. | 6.1, 8.1 |
| API5 | Broken Function Level Authorization | Admin-only endpoints check the admin role on the server. A non-admin calling an admin endpoint must get 403, not 200. | 3.3 |
| API6 | Unrestricted Access to Sensitive Business Flows | Sensitive flows (purchase, refund, coupon, trial, password reset, invite) can't be automated or abused at scale. Rate limits + per-account limits + idempotency where it matters. | 6.1, 7.5 |
| API7 | Server-Side Request Forgery (SSRF) | If the API fetches a user-provided URL, it allows only http(s), rejects non-public addresses, re-checks after redirects, limits size/time. | 5.4 |
| API8 | Security Misconfiguration | No debug endpoints in production, no verbose errors, security headers set, CORS exact allowlist, no default credentials, no sensitive files served. | 3.6, 5.6, 6.2, 10.1–10.4 |
| API9 | Improper Inventory Management | Every route is inventoried: list all routes (including old/deprecated versions) and verify each is either live-and-checked or removed. No shadow/undocumented APIs. Old API versions are retired, not left running. | 3.6, 11.3 |
| API10 | Unsafe Consumption of APIs | Third-party API responses are validated (never trusted blindly), secrets for third-party APIs are server-only, failures fail safely (no crash, no data leak). | 1.1, 5.6 |

## How to audit an API
1. **Inventory first.** List every route (method + path + auth required). If a route isn't in the list, it isn't audited — find it.
2. **Test as two users.** For every object/route, try user A's data as user B. Every cross-user attempt must fail.
3. **Test as no user.** Every private route without a token must fail (401/403, not 200 with empty data).
4. **Test the limits.** Send a huge payload, a huge page size, and rapid requests. Each must be rejected or capped.
5. **Test the old versions.** If v1 exists alongside v2, v1 gets the same checks — or it gets removed.
