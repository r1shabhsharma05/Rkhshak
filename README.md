# Rkhshak (Rakshak) — Master Security Skills

One repo, complete security skills. Nothing partial — every check, every step, verified with evidence before production.

**Works with any agent:** Claude, Codex, and any agent that reads SKILL.md. Each skill is a standard `SKILL.md` (name + description frontmatter) plus `references/`. See `AGENTS.md` for agent instructions.

## Skills

| Skill | What it does | Status |
|---|---|---|
| `security-audit` | Master production-readiness security audit. 85 checks + OWASP Top 10 (web + LLM), multi-agent roles (Auditor / Fixer / Verifier), live probing, evidence standard, deploy gate. | ✅ Ready |
| `security-fix` | Fix security findings with the least code possible. Minimal, complete changes. | ✅ Ready |
| `design-unslop` | Master design skill. Build a screen/app so it never looks vibe-coded, or transform a vibe-coded app into a massive design. Unslop passes, Hallmark themes + floor, art direction, Awwwards bar, lib-first components. | ✅ Ready |
| `code-humanizer` | Write code that reads like a human wrote it. Remove AI tells (verbose comments, generic names, over-abstraction), use human style, rewrite AI code to pass review. | ✅ Ready |
| `minimal-code` | Write the least code that solves the problem. Delete first, use the library, no dead code, no speculation. Smallest complete change. | ✅ Ready |
| `skill-evolution` | Train any agent skill like a neural network — epochs, learning rate, validation gates — without touching model weights. Bounded edits, gated acceptance, nightly sleep cycles. | ✅ Ready |

## How to use
1. Copy `skills/security-audit/` into your agent's skills folder (or read `skills/security-audit/SKILL.md` directly).
2. Before any production audit, read the SKILL.md — it tells you when to use it, the multi-agent workflow, the evidence standard, and the gate.
3. The actual checklists live in `skills/security-audit/references/` — run every check, collect evidence, write AUDIT.md.

## References inside security-audit
| File | What it is |
|---|---|
| `pre-launch-audit-85-rules.md` | The 85-check pre-launch audit (core) |
| `owasp-top-10.md` | OWASP Top 10 (web + LLM), mapped to the 85 checks |
| `vibe-code-security-checklist.md` | Two viral vibe-code security checklists, merged + mapped |
| `cloudflare-audit.md` | Cloudflare 6-phase deep-audit workflow (summary) |
| `launch-readiness-checklist.md` | Pre-launch checks (SEO, performance, accessibility, legal) — separate gate |
| `ux-patterns-checklist.md` | 20 SaaS UX patterns — separate gate |
| `regression-tracking.md` | Compare runs over time — new, fixed, regressed, still open |
| `audit-gate.md` | The deploy gate + severity/fix mapping + report format |
| `owasp-api-top-10.md` | OWASP API Security Top 10 (2023), mapped to the 85 checks |
| `mobile-security.md` | Mobile security deep-dive — pinning, root/jailbreak, biometrics, release hardening |
| `ci-integration.md` | Run automatable checks on every PR + GitHub Actions workflow template |
| `threat-model.md` | STRIDE threat-model template — run before the audit |
| `incident-response.md` | 6-step incident playbook + key-leak and data-exposure steps |
| `compliance-mapping.md` | 85 checks mapped to GDPR, DPDP, SOC 2, PCI-DSS |
| `ai-agent-security.md` | Securing the agent itself — prompt injection, tool abuse, least privilege, approval gates |
| `supply-chain-sbom.md` | Dependency audit, lockfile discipline, SBOM (CycloneDX/SPDX), provenance |
| `mastg-mobile-testing.md` | OWASP MASTG mobile testing — MASVS categories, static + dynamic + manual |
| `cloud-misconfig.md` | Cloud console settings — public buckets, IAM, secrets, encryption, logging, backups |
| `secrets-scanning.md` | Find secrets in code, history, logs, chat — rotate first, purge second |
| `auth-testing.md` | Attack-test JWT, sessions, OAuth, 2FA, login |
| `container-security.md` | Docker image audit — minimal base, scan, non-root, no secrets in layers |
| `privacy-dataflow.md` | Trace personal data — the map, minimum collection, third parties, retention + deletion |

## References inside security-fix
| File | What it is |
|---|---|
| `fix-patterns.md` | Secure code patterns per vulnerability class — SQLi, XSS, CSRF, IDOR, auth, SSRF, path traversal, XXE, deserialization, secrets, rate limiting |
| `verify-rollback.md` | Prove the fix (re-run the check, regression test, independent verification, live check) + plan the rollback before pushing |
| `secret-rotation.md` | A leaked secret, step by step — rotate first, remove second, purge last, verify, record |
| `hotfix-process.md` | Emergency fix for a live vulnerability — triage, contain, smallest fix, verify on live, disclose |
| `dependency-fix.md` | A vulnerable dependency — upgrade, patch, fork, or replace, in that order |

## References inside design-unslop
| File | What it is |
|---|---|
| `vibe-code-tells.md` | The signs a screen looks AI-generated — audit checklist |
| `design-principles.md` | The Floor (hard rules), house rules, laws of the craft |
| `unslop-passes.md` | Subtract first + the 9 passes in order (spacing → motion) |
| `templates.md` | Deal-3 themes, shapes, site effects, Awwwards quality bar |
| `component-libraries.md` | Lib-first guide — shadcn, kokonutui, astryx, 21st.dev, GSAP, Lenis |
| `modern-web.md` | Platform patterns first — modern web guidance, mandatory-first |
| `design-gate.md` | The ship gate — PASS/FAIL, severity + fix mapping, report format |
| `responsive-checklist.md` | Every breakpoint, touch targets, safe areas |
| `accessibility-checklist.md` | Contrast, keyboard, screen reader, color-blind, motion |
| `content-states.md` | Loading / error / empty / success for every component |
| `performance-budget.md` | LCP/INP/CLS targets, fonts, images, 60fps |
| `screen-templates.md` | Login, dashboard, settings, pricing, checkout, onboarding |
| `dark-mode.md` | Dark mode rules — surfaces, color, text |
| `design-system-lock.md` | The design.md template — lock the system so pages don't drift |
| `design-regression.md` | Before/after + compare runs — new, fixed, regressed, still open |
| `motion-system.md` | Easing, durations, stagger — a motion system |
| `typography-color-system.md` | Concrete type scale + palette derivation method |
| `data-viz.md` | Which chart for which question, honest axes, accessibility |
| `microinteractions.md` | Feedback for every touch — press, toggle, drag, swipe, copy |
| `ux-writing.md` | Microcopy patterns — buttons, errors, empty states, success |
| `handoff.md` | Figma/dev handoff specs — measurements, assets, states, behavior |
| `user-testing.md` | Test with real people — 5-second test, task test |
| `21st-dev-prompts.md` | 21st.dev prompt library — ready-made searches + inspiration briefs |
| `ux-patterns.md` | 20 UX patterns every SaaS needs — the design rule for each |
| `vibe-code-fixes.md` | 20 things to fix on a vibe-coded website — a launch gate |
| `backgrounds.md` | 22 background techniques to make designs less flat |
| `animation-techniques.md` | 20 animation techniques with concrete values |
| `landing-page-design.md` | Landing page structure — hero, social proof, benefits, pricing, FAQ, one action per screen |
| `wcag-checklist.md` | WCAG 2.2 concrete criteria — contrast, keyboard, alt text, touch targets, reduced motion |
| `iconography.md` | A consistent icon system — one set, one stroke, 24px grid, no emoji as icons |
| `design-self-review.md` | Critique your own work before shipping — 5-second test, squint test, every state, phone test |
| `form-design.md` | Forms that users finish — labels visible, inline validation, honest submit, multi-step with progress |
| `layout-grid.md` | Grid systems, spacing scale, composition — 12-col desktop / 4-col mobile, one dominant thing |
| `design-tokens.md` | The design system as code — semantic color, spacing/type/radius/shadow scales |
| `mobile-app-design.md` | Native mobile patterns — bottom tabs, thumb zone, gestures with alternatives, offline states |

## References inside code-humanizer

| File | What it covers |
|---|---|
| `ai-tells.md` | The 12 giveaways that code was AI-written, each with a fix + a pre-ship checklist |
| `human-style.md` | How humans actually write code — comments (WHY not WHAT), naming, structure, errors |
| `humanize-existing.md` | Rewrite AI code to read human — strip, rename, inline, match neighbours, before/after |
| `prose-tells.md` | The 26 AI writing patterns from blader/humanizer (MIT) — for comments, docs, commit messages, READMEs, error messages, UI copy |
| `naming-guide.md` | Human names — domain language, booleans as questions, verbs for functions, no generic names |
| `refactor-readability.md` | Restructure AI code so it reads human — extract, flatten, delete dead code, name the magic numbers |
| `readme-docs-voice.md` | Docs that sound like a person — what/why/how, real commands, no fluff, honest limits, stranger test |
| `commit-messages.md` | Human commit messages — lowercase, short, imperative, what + why not how |
| `error-messages.md` | User-facing errors — what happened in plain words, what to do next, no codes, no blame |
| `test-naming.md` | Readable tests — names that are sentences about behaviour, with the condition, one behaviour per test |

## References inside minimal-code

| File | What it covers |
|---|---|
| `delete-first.md` | What to delete (dead code, commented code, speculation, one-use wrappers) + how to delete safely |
| `smallest-change.md` | The smallest complete change — one sentence, library first, when minimal is wrong |
| `measure.md` | Prove it — diff size, files touched, new concepts, dead code, pre-ship checks |
| `ponytail.md` | The ponytail method merged — decision ladder, shortcut comments, never-cut list, levels, review/audit/debt modes |
| `abstraction-judgment.md` | AHA — when NOT to abstract: rule of three, same reason to change, clear name, no flag-soup |
| `yagni.md` | You Aren't Gonna Need It — build only what today needs: no speculative features, no config for one value, no dead code |
| `dependency-minimalism.md` | The dependency diet — count them, make each earn its place, one per job, small + maintained |
| `config-minimalism.md` | Config diet — sane defaults, no config for one value, every option has a user, config in one place |
| `api-surface-minimalism.md` | API surface diet — fewest endpoints, fewest params, no speculative endpoints, one shape per resource |

## References inside skill-evolution

| File | What it covers |
|---|---|
| `training-loop.md` | The 6-stage loop (rollout → reflect → aggregate → select → update → evaluate) + epochs + slow/meta update |
| `validation-gate.md` | Held-out gate — strict improvement only, rejected-edit buffer, no-regression mode, split-leakage rules |
| `edit-budget.md` | Textual learning rate (max edits), bounded add/delete/replace, LR schedule, slow/meta update |
| `skillopt-sleep.md` | Nightly offline self-evolution — harvest → mine → replay → consolidate → stage → adopt (human) |
| `skill-transfer.md` | What survives a move (models, harnesses, benchmarks) + honest scope + A/B evalkit (McNemar + bootstrap CI) |

## Principles
- **Complete, not partial.** Every check runs. N/A only with evidence the mechanism doesn't exist.
- **Evidence, not claims.** A check passes only on observed behaviour (live probe or test output).
- **Gate, not report.** Deploy is blocked until the gate passes.
- **Minimal fixes.** Smallest complete change, server-side, verified by an independent agent.
- **Human vs agent split.** What only a human can do is listed as open, never hidden.
- **Graph first.** Build the project graph before reading code; update it after changes. Never read the whole codebase.

## Provenance
Built from the 85-check pre-launch audit (Mayank Shah v2.0), OWASP Top 10 (2025 + LLM), the Cloudflare 6-phase audit workflow, viral pre-launch checklists, and SkillOpt (Microsoft) for skill evolution.
