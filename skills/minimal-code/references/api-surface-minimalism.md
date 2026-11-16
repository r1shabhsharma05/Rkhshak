# API Surface Minimalism — fewest endpoints, fewest params

An API is a promise. Every endpoint, every parameter, every field is something to maintain, secure, document, and never break. The smallest API that solves the problem is the right one.

## The rules
- **Fewest endpoints.** One endpoint that does the job beats three that split it. Before adding an endpoint, ask: can an existing one do this? If yes, don't add it.
- **Fewest parameters.** Every parameter is a validation, a test, and a way to break the call. A required parameter must be required — if the server can figure it out (the user id from the token, the date as today), don't ask for it.
- **No speculative endpoints.** An endpoint nobody calls is deleted. "The mobile app might need it later" is not a caller. An endpoint with zero callers in the logs is dead code with a network port.
- **One version, one shape.** Responses have one shape per resource. Two shapes for the same thing (v1 + v2, or "legacy" + "new") is two APIs to maintain. Version only when the shape must break — and then retire the old one on a date, not "someday".
- **Errors are part of the surface.** Every endpoint documents its errors (what status, what body, what the client should do). An undocumented error is a surprise.
- **No God endpoints.** An endpoint that takes 20 parameters and does 5 things is 5 endpoints wearing a trench coat. Split it.
- **Delete with a date.** When an endpoint is retired, announce the date, return a deprecation header, and remove it on that date. A deprecated endpoint that lives forever is not deprecated — it's permanent.

## The cost of an endpoint
- **Security surface.** Every endpoint is an attack surface: auth, validation, rate limiting, authorization. More endpoints, more to get wrong.
- **Maintenance.** Every endpoint needs tests, docs, monitoring, and a migration path when it changes.
- **Client confusion.** Ten ways to get the same data means the client picks the wrong one, or all of them.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every endpoint has a caller in the logs | An endpoint with zero callers |
| 2 | Parameters are the minimum (server figures out the rest) | The client sends the user id the server already knows |
| 3 | One response shape per resource | Two shapes for the same thing |
| 4 | Errors documented per endpoint | An undocumented error status |
| 5 | No God endpoints (20 params, 5 jobs) | An endpoint doing five things |
| 6 | Retired endpoints removed on their date | A deprecated endpoint that lives forever |
