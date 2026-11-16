# Auth Testing — attack-test login, sessions, OAuth, and 2FA

Checks say "login is protected". Testing proves it. This is how to attack-test authentication the way an attacker would — on the auditor's own app, with authorization.

## JWT testing
- **None algorithm:** a token with `alg: none` and no signature — does the server accept it? It must not.
- **Weak secret:** a token signed with a guessable secret (`secret`, `123456`, the app name). Try the common secrets; if one works, the key is broken.
- **Algorithm confusion:** a token signed with the public RSA key as an HMAC secret (RS256 → HS256). If the server accepts it, the validation is broken.
- **Expired token:** an old token, replayed after logout — does it still work? Logout must invalidate server-side.
- **Tampered claims:** change the `user_id` / `role` in the payload, re-sign with nothing (or with a wrong key). If the server trusts the edited claims, authorization is client-controlled.
- **No expiry:** a token with no `exp` that works forever. Tokens expire; refresh tokens rotate.

## Session testing
- **Session fixation:** log in, note the session id, log out, log in again — is the session id the same? It must rotate on login.
- **Cookie flags:** `HttpOnly`, `Secure`, `SameSite=Lax` (or Strict). Missing flags are findings.
- **Concurrent sessions:** does the app limit sessions per user, and does "log out everywhere" actually kill them all?
- **Token in URL:** is a token ever in a URL (reset link, invite link)? URLs leak into logs, history, and referrers. Tokens in URLs expire fast (minutes, not days) and are single-use.

## OAuth / social login testing
- **Redirect URI:** can the `redirect_uri` be changed to an attacker domain? If yes, the auth code leaks.
- **State parameter:** is `state` present and validated? Without it, CSRF on the login flow works.
- **Code replay:** is an auth code usable twice? It must be single-use.
- **Account linking:** can an attacker link their social account to a victim's account (by email match without verification)?

## 2FA testing
- **Bypass:** is there a path that skips 2FA (an old endpoint, a "remember this device" that never expires, a backup code that never expires)?
- **Brute force:** is the 2FA code rate-limited? A 6-digit code has 1M possibilities — without a limit, it falls in minutes.
- **Recovery:** does the recovery flow (backup codes, email reset) re-impose 2FA, or does it bypass it?

## Password / login testing
- **Rate limiting:** 10+ wrong passwords in a row — does it block, delay, or let you keep trying?
- **User enumeration:** does "wrong password" vs "no such user" give a different response (message, timing, status code)? Same response for both, or the usernames leak.
- **Credential stuffing:** is there bot protection (CAPTCHA / Turnstile) on login? Without it, leaked password lists work.
- **Password policy:** is the policy enforced server-side (not just in the UI)? Is breached-password checking on (HIBP / leaked-password protection)?

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | `alg: none` token rejected | Server accepts an unsigned token |
| 2 | Weak/guessed signing secret fails | A common secret signs a valid token |
| 3 | Tampered claims rejected | Edited `user_id`/`role` trusted |
| 4 | Logout invalidates server-side | Old token works after logout |
| 5 | Session id rotates on login | Same session id across logins |
| 6 | Cookies carry HttpOnly + Secure + SameSite | A flag missing |
| 7 | OAuth `state` validated, redirect URI locked, code single-use | Any of the three missing |
| 8 | 2FA has no bypass and is rate-limited | A skip path exists, or codes aren't limited |
| 9 | Login rate-limited, no user enumeration | Unlimited attempts, or different responses leak users |

## How this maps to the 85 checks
Login/sessions (Area 2) is the 85-check home. This reference is the attack method — the concrete tests that prove each login check.
