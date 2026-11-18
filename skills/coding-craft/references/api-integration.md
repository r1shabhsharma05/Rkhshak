# API Integration — treat external APIs as hostile dependencies

Distilled from two sources, in our own words: api-integration-specialist (MIT) and zod-pro (MIT). Full workflows live in those sources. Use when connecting to an external REST or GraphQL API, building webhook receivers, or reviewing integration code.

## The through-line
Their uptime is not your uptime. Design for the provider having a bad day: auth expiry, rate limits, flaky endpoints, silently changing schemas, webhooks that arrive twice — or never.

## Client wrapper, not scattered calls
All interaction with a provider lives in one module: auth, base URL, headers, serialization, error mapping. Scattered calls across the codebase guarantee inconsistent handling.

## Resilience primitives
Every outbound call gets: a timeout (connect + total), retries with exponential backoff and jitter (only for idempotent or safe operations), and a circuit breaker for sustained failure. Map provider errors to domain errors (`RateLimited`, `AuthFailed`, `NotFound`, `ProviderDown`) — the rest of the code never sees a raw provider error.

## Auth lifecycle
Tokens expire: refresh proactively, before expiry, with a single refresh under concurrency. Store secrets in a secret manager, never log tokens, prefer OAuth with refresh tokens or rotating API keys over long-lived static secrets.

## Rate limits as a budget
Track quota usage from response headers, queue and pace non-urgent calls, prioritize user-facing sync calls over background sync. Hitting 429s in production means the budget was not planned.

## Webhooks: verify, dedupe, acknowledge fast
Verify signatures with the provider's secret (constant-time compare); handle duplicates via idempotency keys (providers retry); respond 200 *before* doing slow work (queue it); tolerate out-of-order delivery.

## Contract vigilance
Providers change schemas without telling you. Validate every response against a schema and fail loudly on mismatch — a silent schema change becomes silent data corruption otherwise. Keep a contract test that runs against the live provider on a schedule.

## Zod: schema-first validation at the boundary
Declare the schema once and get both runtime validation and a static type (`z.infer` — the type follows the schema, never the reverse). Validate API request/response payloads, webhook bodies, form input, and environment variables at startup (fail fast on bad config).
- **Composition:** primitives, objects, arrays, `.optional()`, `.nullable()`, `.default()` — schemas are values, compose freely.
- **Refinements** (`.refine`, `.superRefine`) for cross-field rules; keep them pure and fast.
- **Transforms** convert after validation (string to date, trim, normalize); the inferred output type differs from input — use `z.input`/`z.output` when both matter.
- **Coercion** (`z.coerce.number()`) parses strings at the HTTP boundary, where everything is a string.
- **Discriminated unions** (`z.discriminatedUnion`) for tagged payloads: webhook events, polymorphic responses.
- **Unknown keys:** strip (default, forgiving), strict (reject — good for catching typos in configs), passthrough (keep). Choose deliberately.
- **Errors:** structured `issues` with paths; map them to form fields or log them with the path attached.

## Common pitfalls
- Retrying a non-idempotent operation (a payment, a create) without an idempotency key.
- Logging a token, a key, or a full webhook body containing secrets.
- Trusting a response shape because it matched once — validate every time.
- No timeout: one slow provider hangs your whole request.
