# Hardening Controls — what to check while you audit

Hardening asks "can an attacker read or break it?" before the audit asks "did it fail a check?" Use this file during the audit (workflow step 3) as a control checklist, and as a source of fix directions to hand to the Fixer. Code patterns for the fix side live in `security-fix/references/boundary-fix-patterns.md`.

## Threat model first

Controls bolted on without a threat model are guesses. Before hardening, spend five minutes thinking like an attacker (see also `references/threat-model.md`):

1. **Map the trust boundaries.** Where does untrusted data cross into the system? HTTP requests, form fields, file uploads, webhooks, third-party APIs, message queues, and **model/LLM output** — plus local values that look internal because the OS handed them to you: another process's command line or environment, filenames on a shared volume, a path in a job payload. Trust follows who *wrote* a value, not which channel delivered it. Every boundary is attack surface.
2. **Name the assets.** What is worth stealing or breaking? Credentials, personal data, payment data, admin actions, money movement.
3. **Run STRIDE over each boundary** — a quick lens, not a ceremony: Spoofing (can someone impersonate a user or service?), Tampering (can data be altered in transit or at rest?), Repudiation (can an action be denied later?), Information disclosure (can data leak?), Denial of service, Elevation of privilege.

## The controls to verify

### Injection, XSS, and access control

- Every query is parameterized. No SQL, NoSQL, or shell command is built from input strings.
- Output is encoded through the framework's auto-escaping. Raw HTML, if unavoidable, passes an allowlist sanitizer first.
- **Authorization** is checked on every request, not just authentication: the authenticated user must own, or be permitted on, the specific resource (A01 / IDOR).

### Authentication and sessions

- Passwords are hashed with a slow, salted function (bcrypt ≥ 12 rounds, scrypt, or argon2). The session secret comes from the environment, never from code.
- Session cookies are `httpOnly`, `secure`, and `sameSite: 'lax'` or `'strict'`, with a bounded lifetime.

### Headers, CORS, and responses

- Security headers on every response; content-security policy starts from `default-src 'self'` and is tightened, not loosened.
- CORS is restricted to an explicit origin list from configuration. Never `*` with credentials.
- Sensitive fields (password hashes, reset tokens) are stripped before any response. Error bodies are generic; internals go to server logs only.

### Input validation and uploads

- Input is validated at the boundary with a schema: allowlisted shape, lengths, enums, formats. Downstream code uses only the parsed, typed value.
- Uploads: allowlisted content types, capped size, content verified (magic bytes) when it matters. The file extension proves nothing.

### Server-side fetches (SSRF)

Any URL the user influences — webhooks, import-from-URL, image proxies, link previews — can be aimed at internal services. Require: allowlisted scheme and host, resolve **all** DNS records and reject any private or reserved address (loopback, link-local, private, unique-local, IPv4 and IPv6), and forbid redirects. That check still has a DNS-rebinding gap: for high-risk surfaces, pin the resolved address or put a filtering agent in front.

### Destructive operations on derived paths

A delete, move, or overwrite is only as safe as the value naming its target, and trust follows who *wrote* that value. A shape check proves well-formedness, not authorization. Before the call, require all three: the resolved target (symlinks resolved) sits under an **allowlisted root**; it is at least one level **below** that root; and it carries **ownership evidence read before the operation**. On refusal, log the rejected target and stop; never fall back to a broader default path.

### Rate limiting

Limit the API generally and auth endpoints strictly. Once more than one process serves traffic, in-memory counters silently become per-instance limits or never fire on serverless: back the limiter with a shared store.

### Secrets

Secrets come from the environment. A committed example file carries placeholders only; real environment files and key material are ignored by version control; the staged diff is grepped before committing. **A secret that reaches a remote is compromised the moment it lands: rotate it first, then purge history** (see `references/secrets-scanning.md` and `secret-exposure-verify.md`).

### Dependencies and supply chain

- Run the native audit against the committed lockfile before every release. Triage critical/high by **reachability** (runtime, build, test, deploy paths). Never apply forced remediation automatically — preview, read changelogs, test each upgrade. Document every deferral with a reason and a review date.
- Audits only match known advisories. They do not catch a newly malicious or typosquatted package. Review new dependencies, lockfile diffs, and install-script changes together: ownership, maintenance, release age, provenance, transitive graph. Block dependency install scripts before first execution; inspect, approve only the minimum, commit the policy, then verify with a clean frozen install. Never blanket-approve.

### Personal data and privacy

Hardening asks "can an attacker read it?" Privacy asks "should *we* hold it at all, and for how long?" The cheapest data to protect is the data never collected.

- **Classify fields as they are added** (non-personal, personal, sensitive) and handle each class accordingly.
- **Collect only against a stated purpose.** "Might be useful later" is breach scope, not a purpose. Keep personal data out of telemetry.
- **Set retention up front, then actually delete.** Every personal-data store needs a lifetime and a working deletion path, including backups, caches, search indexes, and analytics copies.
- **Support the data-subject rights the jurisdiction requires** (export, correct, delete). Design the schema so a user's data is findable and erasable.
- **Consent gates collection and third-party sharing, and is auditable.** Sending personal data to an analytics, ad, or model vendor is sharing; the vendor needs a data-processing agreement.

### AI / LLM features

Calling a model — chatbots, summarizers, agents, retrieval — adds a new attack surface; map it to the OWASP Top 10 for LLM Applications (2025):

- **Model output is untrusted input.** Never into `eval`, SQL, a shell, raw HTML, or a file path; parse defensively, validate against a schema, then encode.
- **Prompts can be hijacked.** Untrusted text in the context — a user message, a fetched page, a document — can carry instructions. The system prompt is not a security boundary; enforce permissions in code.
- **Keep secrets, other tenants' data, and the full system prompt out of the context window**; scope tool permissions, validate every tool argument, confirm destructive actions; cap tokens, request rate, and recursion depth; partition retrieval embeddings per tenant and validate documents before indexing.

## Red flags (any one of these is a finding, not a note)

- User input passed directly to database queries, shell commands, or HTML rendering.
- A delete, move, or overwrite whose target comes from a payload, a config value, or another process's command line, guarded only by a shape check.
- Secrets in source code or commit history; API endpoints without authentication or authorization checks.
- Missing CORS configuration or wildcard origins; no rate limiting on auth endpoints, or an in-memory limiter in front of more than one instance.
- Stack traces or internal errors exposed to users; dependencies with known critical vulnerabilities.
- Server fetches of user-supplied URLs without an allowlist; model output passed into a query, the DOM, a shell, or `eval`.
- Secrets, personal data, or the full system prompt placed inside a model context window.
- Personal data collected with no stated purpose, retention limit, or deletion path; "delete my account" that only flips a flag while the data lingers.

## Common rationalizations (all false)

| Rationalization | Reality |
|---|---|
| "This is an internal tool, security doesn't matter" | Internal tools get compromised. Attackers target the weakest link. |
| "We'll add security later" | Retrofitting is far harder than building it in. Add it now. |
| "No one would try to exploit this" | Automated scanners will find it. Obscurity is not security. |
| "The framework handles security" | Frameworks provide tools, not guarantees. They still have to be used correctly. |
| "It's just a prototype" | Prototypes become production. |
| "Threat modeling is overkill here" | Five minutes of "how would I attack this?" prevents design flaws no control can patch later. |
| "It's just model output, it's only text" | That text can be a SQL statement, a script tag, or a shell command. |
| "The audit passed, so the dependency is safe" | Audits match known advisories. They do not detect a newly malicious package. |
| "Collect it now, we might need it later" | Data you don't hold can't be breached. |

## How this maps to the 85 checks

These controls underpin Areas 1–6 (secrets, login/sessions, access control, DB/storage, input/output, API abuse), Area 8 (AI), Area 9 (dependencies), and Area 12 (privacy) of `references/pre-launch-audit-85-rules.md`. A control missing here is a finding there — record it with evidence, not as advice.

## Provenance

Summarised in our own words from the security-and-hardening skill (threat-model-first hardening, OWASP Top 10 prevention patterns) and the OWASP Top 10 for LLM Applications (2025).
