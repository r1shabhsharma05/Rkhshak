# Rkhshak (Rakshak) — Master Security Skills

One repo, complete security skills. Nothing partial — every check, every step, verified with evidence before production.

## Skills

| Skill | What it does | Status |
|---|---|---|
| `security-audit` | Master production-readiness security audit. 85 checks + OWASP Top 10 (web + LLM), multi-agent roles (Auditor / Fixer / Verifier), live probing, evidence standard, deploy gate. | ✅ Ready |
| `security-fix` | Fix security findings with the least code possible. Minimal, complete changes. | ✅ Ready |

## How to use
1. Copy `skills/security-audit/` into your agent's skills folder (or read `skills/security-audit/SKILL.md` directly).
2. Before any production audit, read the SKILL.md — it tells you when to use it, the multi-agent workflow, the evidence standard, and the gate.
3. The actual checklists live in `skills/security-audit/references/` — run every check, collect evidence, write AUDIT.md.

## References inside security-audit
| File | What it is |
|---|---|
| `pre-launch-audit-85-rules.md` | The 85-check pre-launch audit (core) |
| `owasp-top-10.md` | OWASP Top 10 (web + LLM), mapped to the 85 checks |
| `secureguard-hardening-checklist.md` | 46-item hardening checklist (SecureGaurd Day 3, verified live) |
| `vibe-code-security-checklist.md` | Two viral vibe-code security checklists, merged + mapped |
| `cloudflare-audit.md` | Cloudflare 6-phase deep-audit workflow (summary) |
| `launch-readiness-checklist.md` | Pre-launch checks (SEO, performance, accessibility, legal) — separate gate |
| `ux-patterns-checklist.md` | 20 SaaS UX patterns — separate gate |
| `audit-gate.md` | The deploy gate + report format |

## Principles
- **Complete, not partial.** Every check runs. N/A only with evidence the mechanism doesn't exist.
- **Evidence, not claims.** A check passes only on observed behaviour (live probe or test output).
- **Gate, not report.** Deploy is blocked until the gate passes.
- **Minimal fixes.** Smallest complete change, server-side, verified by an independent agent.
- **Human vs agent split.** What only a human can do is listed as open, never hidden.
- **Graph first.** Build the project graph before reading code; update it after changes. Never read the whole codebase.

## Provenance
Built from battle-tested audits: the 85-check pre-launch audit (Mayank Shah v2.0) that took SafeLife from 27/85 to 61/85, OWASP Top 10 (2025 + LLM), and hardening checklists verified live on production apps.
