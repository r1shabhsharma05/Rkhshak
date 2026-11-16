# Audit Gate + Report Format

## The gate (deploy is blocked until it passes)
- **Bar:** every applicable check PASSES. N/A counts only when the mechanism genuinely does not exist, with evidence of the search that proved it.
- **Counts to report:** Passed · Fixed (with evidence) · Still open · Needs human · N/A · Can't verify.
- **Max achievable is less than the total** when some checks are genuinely N/A — report the max, not the raw total, so the gate is honest.
- **A gate is NOT passed while:** any Critical/High is open, any NEEDS-HIM item is open, or any fixed check lacks fresh verification evidence.
- **Re-run the full audit after every fix round.** A fix is not "done" until the Verifier re-ran its check with fresh evidence.

## Severity + fix mapping
Every finding carries a severity and a fix route. Severity decides the gate; the fix route decides who fixes it and how.
- **Critical** — unauthenticated actor gains code execution, full data-store access, or takeover of arbitrary accounts. Blocks the gate. Fix: `security-fix` skill, smallest complete change, Verifier re-runs the check.
- **High** — an actor fully defeats an explicit security control with real consequences (auth bypass, cross-tenant read/write, stored script execution, authenticated code execution, unauthenticated remote stop of a shared service). Blocks the gate. Fix: `security-fix` skill.
- **Medium** — a real boundary violation with limited blast radius or uncommon preconditions. Blocks the gate until fixed or the user explicitly risk-accepts it in writing (record the acceptance, the reason, and the expiry).
- **Low** — disclosure of non-secret internals, or an effect requiring sustained effort for minimal gain. Does not block the gate, but must be listed.
- **Informational** — a confirmed but minimal-impact observation. Listed only.
- A finding with no demonstrated boundary violation and no concrete result gets no severity — it is not a finding, it is a note. Never assign severity to a `needs_validation` record.
- Every Critical/High/Medium finding must name its fix: the file(s) to change, the invariant to enforce, and the check that will verify it. The `security-fix` skill does the fix; the Verifier confirms it.

## Roles (summary)
- **Auditor:** runs checks, collects evidence, writes AUDIT.md. Fixes nothing.
- **Fixer:** fixes only user-approved findings, smallest complete change each.
- **Verifier:** independently re-runs every fixed check with fresh evidence. Fixes nothing, trusts no claim without evidence.

## Final report format (one screen)
1. **Verdict** — one line, e.g. "Ready to launch after 2 High fixes" or "Not ready: 3 Critical issues open". Never "100% secure".
2. **Counts** — Passed · fixed · still open · need you · skipped (N/A with reason).
3. **Open issues** — one line each, Critical first, with who fixes it (AI or user).
4. **Your to-do list** — every checklist item that's still open.
5. **Do this on your live app** — every fix that changed data, a secret, env, or config, with exact steps to repeat it on live.
6. **If a key leaks** — 5 steps for this app: which key, where to revoke it, where to update it, re-publish, then check the bill/credit usage.
7. **Security contact** — a way to report issues (security.txt or an email) and who acts if something goes wrong and how affected users are told.
8. **Clean up AUDIT.md** — it lists the app's weaknesses; delete it once fixes are done.
9. **When to re-run** — before every major release, after adding payments, uploads, AI, or a new integration, and every 3 months.

End every final report with: "This audit catches the most common and most damaging mistakes, but it isn't a professional penetration test. Before you handle payments or sensitive data at scale, get a human security review."
