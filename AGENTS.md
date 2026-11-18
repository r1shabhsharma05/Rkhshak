# AGENTS.md — for AI agents using Rkhshak

This repo's skills work with **any agent that reads SKILL.md** — Claude, Codex, and others. There is no agent-specific code. Follow the open Agent Skills format: each skill is a `SKILL.md` with `name` + `description` frontmatter, plus `references/` files it points to.

## How to use a skill
1. Read the skill's `SKILL.md` in full before acting. It tells you when to use it, the workflow, and the rules.
2. Follow the workflow exactly. Do not skip steps, do not invent checks, do not weaken security.
3. Read the `references/` files the SKILL.md points to when the workflow says so. They carry the checklists, the gate, and the report format.
4. If the skill names a role (Auditor / Fixer / Verifier), keep the roles separate. The agent that finds a problem never verifies its own fix.

## Available skills
| Skill | Path | Use when |
|---|---|---|
| `security-audit` | `skills/security-audit/SKILL.md` | Audit, security-check, or verify production readiness; before any production deploy/launch. |
| `security-fix` | `skills/security-fix/SKILL.md` | Fix a security finding the user approved, with the least code possible. |
| `pentest` | `skills/pentest/SKILL.md` | Pentest, hack, security-test, or exploit-test your own app, API, or repo — active exploitation with proof. Staging first, authorized targets only. |
| `design-unslop` | `skills/design-unslop/SKILL.md` | Design a screen/app so it never looks vibe-coded, or transform a vibe-coded app into a massive design. |
| `code-humanizer` | `skills/code-humanizer/SKILL.md` | Write code that reads like a human wrote it — remove AI tells, use human style, rewrite AI code to pass review. |
| `minimal-code` | `skills/minimal-code/SKILL.md` | Write the least code that solves the problem — delete first, use the library, no dead code, no speculation. |
| `skill-evolution` | `skills/skill-evolution/SKILL.md` | Improve any agent skill like training a neural network — epochs, learning rate, validation gates, nightly sleep cycles. |
| `spec-kit` | `skills/spec-kit/SKILL.md` | Build a feature or project spec-first, or run the bug / idea-assessment extensions. |
| `motion-craft` | `skills/motion-craft/SKILL.md` | Animate something, fix janky motion, audit/remove motion, or name an effect. |

## Rules that apply to every agent
- Audit/fix only the user's own project. Never touch what the user does not own or has no authorization for.
- Read-only by default. No code, config, database, or setting changes until the user explicitly approves that specific fix.
- Never print a full secret. Show only its first 4 characters + file:line.
- Never ask anyone to paste a secret into chat.
- Never weaken security to make an error go away.
- Evidence, not claims. A check passes only on observed behaviour (live probe or test output).
- Report after every task: outcome + what was done + evidence.
