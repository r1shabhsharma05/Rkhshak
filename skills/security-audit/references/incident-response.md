# Incident Response — what to do when something goes wrong

A breach is not the time to figure out the plan. Write this playbook before you need it. When an incident happens, follow it in order.

## The 6 steps (in order — never skip ahead)
1. **Detect + confirm.** What happened, when, what is affected? Confirm it is real (not a false alarm) with evidence: logs, alerts, a user report. Write down the time you confirmed it.
2. **Contain.** Stop the bleeding first. Options (pick what fits): rotate the leaked key/secret immediately, revoke the affected tokens/sessions, block the attacking IP/account, take the affected endpoint offline, disable the compromised integration. Containment comes before understanding the full scope.
3. **Eradicate.** Remove the cause: fix the vulnerability, remove the attacker's access (delete their accounts/sessions/keys), clean any backdoor or malicious data.
4. **Recover.** Restore service safely: re-deploy the fix, re-enable the endpoint, verify the fix works (re-run the check that failed), monitor closely for 24–48 hours.
5. **Notify.** Tell the affected users what happened, what data was involved, and what they should do. Tell them promptly and honestly — never hide a breach. If the law requires it (GDPR 72 hours, DPDP), notify the regulator too. Keep a record of who was told, when, and what was said.
6. **Learn.** Write a post-mortem within a week: timeline, root cause, what worked, what failed, and the concrete changes (code, process, monitoring) that prevent it next time. File it with the audit reports.

## If a key/secret leaks (the most common incident)
1. **Revoke it first** (at the provider — not just delete it from the code). A deleted-but-live key is still usable.
2. **Replace it** everywhere it was used (code, env vars, CI, preview + live).
3. **Re-deploy** with the new key.
4. **Check the bill/usage** for abuse (unexpected charges, strange API calls, new accounts).
5. **Check the history** — was it ever committed? If yes, it must be rotated (deleting the commit isn't enough) and the history cleaned if possible.

## If user data is exposed
1. **Contain** (revoke access, fix the hole) before anything else.
2. **Scope it:** which users, what data, how many records? Get the number right — don't guess.
3. **Notify** the affected users with specifics (what data, what to do). Offer concrete help (password reset, monitoring).
4. **Preserve evidence** (logs, snapshots) before cleaning up — don't destroy the record of what happened.

## Contacts (fill this in — a playbook without contacts is a wish)
| Role | Who | How to reach them |
|---|---|---|
| Incident lead | <name> | <phone/email> |
| Engineering | <name> | <phone/email> |
| Hosting / DB provider | <provider> | <support link> |
| Payment provider | <provider> | <support link> |
| Users (notification) | <channel> | <email / in-app> |

## Rules
- **Contain before you investigate.** Stopping the damage matters more than understanding it fully.
- **Never hide a breach.** Users and regulators find out anyway. Honest, prompt notification is the only option.
- **Write it down.** Every decision, every action, with timestamps. Memory is not a record.
- **Practice once.** Walk through the playbook (a tabletop exercise) before a real incident. A plan nobody has read is not a plan.
