# Fix Patterns — secure code per vulnerability class

When a finding says "SQL injection" or "XSS", the fix is not a guess. Each vulnerability class has a known-good pattern. Use it verbatim, adapt only the names.

## The patterns

### SQL injection → parameterized queries
Never build a query by concatenating user input. Use placeholders.
```
// WRONG: db.query("SELECT * FROM users WHERE id = " + userId)
// RIGHT: db.query("SELECT * FROM users WHERE id = $1", [userId])
```
If the query must be dynamic (a column name, a sort order), validate it against an allowlist of known-good values. Never parameterize a table or column name — allowlist it.

### XSS → output encoding + CSP
- Encode output for its context: HTML-encode in HTML, JS-encode in scripts, URL-encode in URLs. A template engine that auto-escapes is the default; raw HTML insertion is opt-in and reviewed.
- Content-Security-Policy header as a second layer: no inline scripts, no `eval`, scripts only from named sources.
- Never render user input with `innerHTML` / `dangerouslySetInnerHTML` unless it passed through a sanitizer (DOMPurify or equivalent).

### CSRF → tokens
- State-changing requests (POST/PUT/DELETE) carry an anti-CSRF token tied to the session, verified server-side. SameSite=Lax/Strict cookies as a second layer.
- GET requests never change state.

### Broken access control / IDOR → server-side authorization
- Every request that touches an object checks ownership server-side: "does this user own this id?" The check happens on the server, on every request, not once in the UI.
- Never trust an id from the client without verifying it belongs to the caller. Never hide a button and call it access control.

### Authentication → modern password handling
- Passwords hashed with bcrypt, argon2, or scrypt (never MD5/SHA1/plain). Salted per user, cost factor set so a hash takes ~100ms+.
- Login rate-limited server-side. Lockout or progressive delay after repeated failures. No user enumeration (same response for "wrong password" and "no such user").

### SSRF → one guard, reused for every outbound fetch
- All outbound requests from user-supplied URLs go through ONE guard function (`fetchSafe(url)`). Copy the shape below, adapt only the names. Never hand-roll a second validator per route.
- The guard checks, in order: (1) scheme is http or https only; (2) resolve the host with DNS and reject private, loopback, link-local, or reserved IPs — 10/8, 172.16/12, 192.168/16, 127/8, 169.254/16 (the cloud metadata address lives there), 0.0.0.0/8, ::1, fc00::/7, fe80::/10; (3) follow redirects only by re-running the same guard on the new URL (max 3); (4) timeout (5s) and cap the response size (1 MB — abort past it).
```
// ONE guard — copy this shape, adapt only the names.
// isPrivate() is one small check over the ranges in the bullet above.
async function fetchSafe(url, { maxRedirects = 3, timeoutMs = 5000, maxBytes = 1_000_000 } = {}) {
  const u = new URL(url);
  if (u.protocol !== 'http:' && u.protocol !== 'https:') throw new Error('bad scheme');
  const addrs = await dns.lookup(u.hostname, { all: true });
  if (addrs.some(a => isPrivate(a.address))) throw new Error('blocked host');
  // fetch with redirect: 'manual'; on each Location header, re-run fetchSafe (maxRedirects).
  // AbortSignal.timeout(timeoutMs); abort the body stream once it passes maxBytes.
}
```
- Residual risk — DNS rebinding (TOCTOU): the IP resolved at check time can differ from the IP the fetch connects to. Mitigate by resolving once and connecting to the resolved IP, or record the residual risk in the report. Do not silently ignore it.

### Path traversal → canonicalize + allowlist
- Resolve the user-supplied path to its canonical form, then check it stays inside the allowed directory. Reject `..`, absolute paths, and symlinks that escape.
- Never use user input as a file path without this check.

### XXE → disable external entities
- XML parsers: disable DTDs / external entities entirely. If the parser can't do that, don't parse untrusted XML.

### Insecure deserialization → avoid, or sign
- Don't deserialize untrusted data. If you must, use a format with no code execution (JSON, not pickle/Java serialization) and verify a signature first.

### Secrets → env + rotation
- Secrets come from the environment or a secrets manager, never from code or a committed file. After a leak: rotate the secret, then remove it from history — rotation first, history second (a purge alone does not secure a live token).

### Rate limiting → server-side
- Limits enforced on the server, per user/IP, on every sensitive endpoint (login, OTP, SOS, payments). Client-side limits are decoration.

## How to use this file
1. Find the vulnerability class of the finding.
2. Copy the pattern. Adapt names, not the mechanism.
3. Verify with the check in `references/verify-rollback.md` — re-run the failing check, write a regression test.
4. If no pattern fits the finding, say so. Don't invent one.
