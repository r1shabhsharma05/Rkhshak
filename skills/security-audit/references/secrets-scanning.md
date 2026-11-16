# Secrets Scanning — find the secret before an attacker does

A secret in code, history, logs, or chat is a breach waiting to happen. This is the detection method: how to scan, what to do when one is found, and how to stop the next one.

## What to scan
| Where | What hides there |
|---|---|
| Code + config files | API keys, tokens, passwords, private keys in source, `.env` files, config |
| Git history | Secrets committed in the past, even if deleted from the current files (history keeps them) |
| Logs + error output | Tokens printed in logs, URLs with keys, stack traces with credentials |
| Chat / docs / tickets | Keys pasted in a message, a screenshot of a dashboard, a shared doc |
| CI / build output | Secrets printed in build logs, env vars dumped in debug output |
| Dependencies | A package that exfiltrates env vars at install time (check install scripts) |

## Tools
- **gitleaks** — scans git history + files for secrets (fast, free, runs in CI).
- **trufflehog** — scans git history, files, and cloud accounts for verified secrets (checks if the key is live).
- **GitHub secret scanning** — built-in, alerts on known secret formats in the repo (enable it; push protection stays off unless the user asks for it).
- **Manual grep** — for the patterns tools miss: `AKIA`, `ghp_`, `sk-`, `xox`, `-----BEGIN`, `password =`, `api_key`.

## The scan (run on every audit)
1. Run gitleaks (or trufflehog) over the full history, not just HEAD. A secret deleted from the current files is still in history.
2. Grep the current tree for high-entropy strings and known prefixes.
3. Check CI logs and error output for printed secrets.
4. List every finding: what it is, where it is (file:line or commit), whether it is live.

## When a secret is found — the order matters
1. **Rotate/revoke FIRST.** The secret is dead before anything else happens. A purge alone does not secure a live token — anyone who already copied it can still use it.
2. **Remove it from the code** — replace with an env var / secrets manager reference.
3. **Purge it from history** — only after rotation, and only with the user's approval (rewriting history is destructive; it needs a force-push and every collaborator must re-clone).
4. **Verify** — the old secret no longer works (try it, watch it fail), the new secret works, the scan is clean.

## What counts as a finding
- A live secret anywhere (code, history, logs, chat) = Critical until rotated.
- A revoked secret still in history = Low (after rotation) — but it must still be purged, because the value is visible.
- A false positive (a test key, a placeholder like `sk-...`, an example in docs) = N/A, with the reason recorded. Never silently drop it.

## Prevention
- Pre-commit hook: scan before every commit (gitleaks pre-commit).
- CI gate: scan on every PR — a PR that adds a secret fails the check.
- `.gitignore` for `.env`, keys, and credentials — and verify it works (a file in `.gitignore` that was already committed is still tracked).
- Never ask anyone to paste a secret into chat. Secure entry only.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Full-history scan clean (or every finding rotated + recorded) | A live secret in history, unrotated |
| 2 | Current tree clean | A secret in a file right now |
| 3 | Logs + CI output clean | A secret printed in a log |
| 4 | Pre-commit + CI scanning enabled | No scan runs before code lands |
| 5 | `.gitignore` covers secrets and actually works | An env/key file tracked in git |
| 6 | Every found secret rotated BEFORE purge | Purge done (or planned) without rotation |

## How this maps to the 85 checks
Secrets (Area 1) is the 85-check home. This reference is the method — the tools, the scan, and the rotate-first order.
