# Rkhshak (Rakshak) — Master Skills

One repo, complete skills. Nothing partial — every check, every step, verified with evidence before production.

**Works with any agent:** Claude, Codex, and any agent that reads SKILL.md. Each skill is a standard `SKILL.md` (name + description frontmatter) plus `references/`. See `AGENTS.md` for agent instructions.

## Skills

| Skill | What it does | Status |
|---|---|---|
| `security-audit` | Master production-readiness security audit. 85 checks + OWASP Top 10 (web + LLM), multi-agent roles (Auditor / Fixer / Verifier), live probing, evidence standard, deploy gate. | ✅ Ready |
| `security-fix` | Fix security findings with the least code possible. Minimal, complete changes. | ✅ Ready |
| `pentest` | Actively test a web app, API, or codebase by attempting real exploits and proving each finding with a working proof-of-concept. Staging first, authorized targets only. | ✅ Ready |
| `design-unslop` | Master design skill. Build a screen/app so it never looks vibe-coded, or transform a vibe-coded app into a massive design. Unslop passes, Hallmark themes + floor, art direction, Awwwards bar, lib-first components. | ✅ Ready |
| `code-humanizer` | Write code that reads like a human wrote it. Remove AI tells (verbose comments, generic names, over-abstraction), use human style, rewrite AI code to pass review. | ✅ Ready |
| `minimal-code` | Write the least code that solves the problem. Delete first, use the library, no dead code, no speculation. Smallest complete change. | ✅ Ready |
| `skill-evolution` | Train any agent skill like a neural network — epochs, learning rate, validation gates — without touching model weights. Bounded edits, gated acceptance, nightly sleep cycles. | ✅ Ready |
| `spec-kit` | Spec-driven development: specifications drive code — constitution → specify → clarify → plan → tasks → analyze → implement → converge, plus bug and idea-assessment extensions. | ✅ Ready |
| `motion-craft` | Build, review, audit, or remove UI motion so it feels right — frequency gate, purpose, tool ladder, springs, frame-budget performance, vocabulary, native motion. | ✅ Ready |
| `seo` | Audit, plan, or improve search visibility — site/page audits, technical, content, schema, local, GEO, agent readiness. | ✅ Ready |
| `instagram-craft` | Plan, write, and review Instagram content — Reels, carousels, captions, Stories, profile, comments, DMs. Draft only, never auto-posts. | ✅ Ready |
| `youtube-craft` | Plan, write, package, and review YouTube videos — scripts, titles, retention, chapters, Shorts. Draft only, never publishes. | ✅ Ready |
| `coding-craft` | Write, test, debug, review, and verify code — TDD, debugging, five-axis review, verification before done, APIs, docs. | ✅ Ready |
| `ship-workflow` | Take work from idea to production — plan, constrain, dispatch, execute, scope, git, CI/CD, launch, OSS PRs. | ✅ Ready |
| `codebase-intelligence` | Understand a codebase before touching it — graph mapping, official docs, history, corrections into rules. | ✅ Ready |
| `job-search` | Find roles, score fit honestly, tailor CV + cover letter, verify the submission landed, prep for interviews, negotiate pay, write contracts. | ✅ Ready |
| `lead-gen` | Find evidence-backed first customers and leads from public signals, draft outreach that is never sent, verify contact details honestly. | ✅ Ready |
| `video-craft` | Direct and produce short videos — stickman, premium reels, HTML-to-video, code-to-video, full-pipeline — analyse video, generate voiceover. | ✅ Ready |
| `linkedin-craft` | Plan, draft, audit, and humanise LinkedIn posts, comments, replies, and profiles — DRAFT ONLY, the owner posts himself. | ✅ Ready |
| `multi-agent-team` | Run one owner and a team of specialist agents as a single unit — one command in, research gated by the whole team, a human-readable plan, execution with a test after every step, and nothing ships without the owner's pass. | ✅ Ready |

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
| `appsec-plan.md` | "Make my application secure" — map assets, pick the right test per asset, one ranked plan |
| `hardening-controls.md` | Threat-model-first controls — boundaries, SSRF, destructive paths, secrets, dependencies, personal data, model output |
| `deploy-authorization.md` | Build and deploy are separate approvals — publish only on an explicit deploy word |
| `secret-exposure-verify.md` | Prove "no leak" — every path, history, remote raw-URL check |
| `deep-audit-safety.md` | Sandboxed execution, coverage ledger, prior-run handling, budget gate |

## References inside security-fix
| File | What it is |
|---|---|
| `fix-patterns.md` | Secure code patterns per vulnerability class — SQLi, XSS, CSRF, IDOR, auth, SSRF, path traversal, XXE, deserialization, secrets, rate limiting |
| `verify-rollback.md` | Prove the fix (re-run the check, regression test, independent verification, live check) + plan the rollback before pushing |
| `secret-rotation.md` | A leaked secret, step by step — rotate first, remove second, purge last, verify, record |
| `hotfix-process.md` | Emergency fix for a live vulnerability — triage, contain, smallest fix, verify on live, disclose |
| `dependency-fix.md` | A vulnerable dependency — upgrade, patch, fork, or replace, in that order |
| `pentest-fix-verify.md` | Fix a finding proven by a pentest — re-run the exploit to prove it is dead |
| `boundary-fix-patterns.md` | Schema validation, file uploads, destructive paths, model output, data minimization |

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
| `art-direction.md` | Idea from the subject — inventory, argument, idea sentence, look-and-fix loop |
| `page-structures.md` | Anatomy by job, 21 macrostructures, scroll choreography, brand truth |
| `interaction-polish.md` | Component interaction polish — press feedback, popover origin, tooltip timing |
| `platform-design.md` | Platform review — eight principles, five lenses, Liquid Glass rules |
| `stress-test-ui.md` | Worst-case data stress test — toggle, failure signatures, truncate/wrap/clamp |
| `reference-lookups.md` | Design-intelligence lookups — palettes, pairings, guidelines; verify before applying |
| `webgl-3d.md` | Three.js only with purpose — minimal scene, model loading, performance rules, static poster |

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

## References inside spec-kit

| File | What it is |
|---|---|
| `constitution.md` | The 9 articles, versioning, amendment |
| `capability-map.md` | Phase 0 — module table + build order |
| `specify.md` | Writing the spec — WHAT + WHY, NEEDS CLARIFICATION, template, quality checklist |
| `clarify.md` | Up to 5 questions, one at a time, answers encoded back |
| `plan.md` | Research, data model, contracts, quickstart, constitution gates |
| `tasks.md` | Checklist task format, [P] markers, phases by user story |
| `analyze.md` | Read-only cross-artifact check, severity, report format |
| `checklist.md` | Checklists as unit tests for requirements writing |
| `implement.md` | Phase-by-phase execution, checklist gate, marking tasks done |
| `converge.md` | Append-only gap closure, converged report, repeat loop |
| `bug-extension.md` | Assess → fix → verify, verdict verified / partial / failed |
| `assess-extension.md` | Intake → research → define → shape → decide (go / needs-clarification / kill) |
| `scaffolding.md` | New vs existing project setup, the specify CLI |

## References inside pentest

| File | What it is |
|---|---|
| `pentest-method.md` | Two run modes, budgets, exit codes, results |
| `web-app-pentest.md` | Black-box live-app pentest |
| `api-pentest.md` | Schema-driven API pentest, BOLA proof |
| `code-pentest.md` | White-box code pentest |
| `owasp-pentest-coverage.md` | OWASP Top 10:2025 testability |
| `ci-pentest-gate.md` | Diff-scoped PR gate |
| `managed-continuous.md` | Managed/continuous testing |

## References inside motion-craft

| File | What it is |
|---|---|
| `build-sequence.md` | Build sequence + Never Ship list |
| `physical-motion.md` | Springs, gestures, velocity handoff |
| `motion-performance.md` | Frame budget, symptom table, will-change |
| `motion-vocabulary.md` | Reverse-lookup glossary |
| `motion-audit.md` | Audit, review bar, removal |
| `native-motion.md` | Expo/React Native motion |

## References inside seo

| File | What it covers |
|---|---|
| `references/audit-and-scoring.md` | Full-site and single-page audit process, the 0–100 score weights, priority definitions, report structure, error handling |
| `references/technical.md` | Crawlability, indexability, security flags, URLs, mobile parity, Core Web Vitals, rendering, IndexNow, JS SEO traps |
| `references/content-and-eeat.md` | Who/How/Why, E-E-A-T, content metrics, AI-content assessment, draft cleanup, citation readiness, freshness |
| `references/content-briefs-and-clusters.md` | Content briefs, SERP-overlap clustering, hub-and-spoke, intent, internal-link matrix |
| `references/schema-and-sitemap.md` | Schema type status (active / retired / deprecated), JSON-LD generation, sitemap rules and limits |
| `references/images.md` | Image optimisation (alt, size, format, responsive, lazy, CLS) and generated SEO image assets |
| `references/backlinks.md` | Backlink profile, anchor distribution, toxic links, competitor gap, free data sources |
| `references/local-and-maps.md` | Local SEO (GBP, reviews, NAP, citations, local schema) and Maps intelligence (geo-grid, radius, review signals) |
| `references/international.md` | Hreflang validation, generation, implementation methods, common mistakes |
| `references/geo-and-agentic.md` | GEO citability scoring, AI crawler table, brand signals, agent readiness (Lighthouse, llms.txt, WebMCP) |
| `references/live-data.md` | Google API tiers, DataForSEO commands, cost guardrails, what each source can and cannot prove |
| `references/plan-and-scale.md` | Strategic plan phases, programmatic SEO gates, e-commerce, SXO, FLOW, drift monitoring, site-quality gate |

## References inside instagram-craft

| File | What it covers |
|---|---|
| `references/plan-and-voice.md` | Weekly plan, voice profile, log and swipe files, engagement round |
| `references/reel.md` | Reel shape, hook formulas, script, beats, on-screen text, rules |
| `references/carousel-and-caption.md` | Carousel structure and files; caption jobs, hashtags, search terms, linter |
| `references/story.md` | Daily Stories shape, stickers, DM funnel |
| `references/engagement.md` | Comments on others, replies under your own posts, DMs and follow-ups |
| `references/profile.md` | Profile scoring rubric and rewrite order |
| `references/audit-and-research.md` | Post-mortem audit metrics; viral research and the swipe file |
| `references/repurpose.md` | Extracting posts from one long asset |
| `references/human-voice.md` | Humaniser, detection panel, what the tools do and do not prove |

Scripts in `scripts/`: reel-hooks.json (26 formulas), reel-hookscore.py, reel-beats.py, caption.py, humanize.py, detect.py, slop.json, swipe.py, profile-rubric.json.

## References inside youtube-craft

| File | What it covers |
|---|---|
| `references/plan-and-voice.md` | Weekly plan, voice profile, capacity honesty |
| `references/script-and-hooks.md` | Script shape, 21 hook formulas, scoring, retention beats |
| `references/package-and-seo.md` | Title + thumbnail as one unit; description, tags, query test |
| `references/retention-and-edit.md` | Retention diagnosis, edit decision lists, chapters |
| `references/shorts-and-repurpose.md` | Shorts from long video; what survives without context |
| `references/audit-and-research.md` | Channel audit (one fix); viral research by channel-relative multiple |

Scripts in `scripts/`: hooks.json (21 formulas), hookscore.py, title.py, retention.py, deadair.py, chapters.py, swipe.py.

## References inside coding-craft

| File | What it covers |
|---|---|
| `references/tdd.md` | Red-green-refactor, prove-it bug pattern, test pyramid, good-test rules |
| `references/debugging.md` | Stop-the-line, reproduce → localize → reduce → fix → guard → verify, three-fix rule |
| `references/code-review.md` | Five-axis review, review process, receiving and requesting review, feedback loop |
| `references/verification.md` | Iron law — run it fresh, read the output, claim only what it proves |
| `references/simplification.md` | Simplify without changing behaviour — principles, process, language notes |
| `references/api-design.md` | Contract-first API and interface design — REST, types, idempotency |
| `references/api-integration.md` | Resilient third-party integration + Zod validation at boundaries |
| `references/dependencies.md` | Dependency diagnosis, deprecation, and migration patterns |
| `references/performance.md` | Measure → bottleneck → fix → verify → guard, with targets |
| `references/observability.md` | Define working, signals, logs, metrics, traces, alerts, runbooks |
| `references/testing-in-browser.md` | Playwright patterns + DevTools debugging workflow |
| `references/docs-and-decisions.md` | ADRs, comments, API docs, README, changelog, first-reader check, teach-back |
| `references/platform-notes.md` | Mobile-native feel, Swift, typed AI integration |

## References inside ship-workflow

| File | What it covers |
|---|---|
| `references/shape-the-idea.md` | Brainstorming, idea refinement, thinking-out-loud echo |
| `references/planning.md` | Plan mode, dependency graph, vertical slices, tasks, checkpoints |
| `references/constraints.md` | Written quality bar — floors, numbers, ratchets, guarding the bar |
| `references/adversarial-review.md` | Doubt-driven review + fresh-context (Elephant–Goldfish) design review |
| `references/executing.md` | Executing a plan — task loop, completion contract, final review |
| `references/dispatching.md` | Dispatching parallel agents — pattern, briefs, subagent execution, ledger |
| `references/incremental.md` | Thin verifiable slices + scope-creep detection on diffs |
| `references/git-workflow.md` | Trunk-based git, atomic commits, worktrees, finishing a branch |
| `references/ci-cd.md` | Quality-gate pipeline, GitHub Actions, deploy strategies, environments |
| `references/oss-prs.md` | Open-source PR pipeline + fork PR handoff |
| `references/launch.md` | Pre-launch checklist, flags, staged rollout, rollback, error budget |
| `references/vercel.md` | Vercel cost/performance optimisation + preview environment parity |
| `references/platform-ship.md` | Shipping a Chrome extension (MV3 + store) and an Expo app (EAS + stores) |

## References inside codebase-intelligence

| File | What it covers |
|---|---|
| `references/graphify.md` | Build/query a codebase knowledge graph — callers, impact, paths, hubs, explanations |
| `references/trail-code.md` | Session learning trails on top of the graph — what was learned, what to re-check |
| `references/source-driven.md` | Ground every decision in official docs — detect stack, fetch, implement, cite |
| `references/commit-archaeology.md` | Reconstruct why code exists from git history, with evidence rules |
| `references/learn-taste.md` | Turn corrections into lasting rules, with their why |
| `references/context-packing.md` | Context hierarchy, packing strategies, budget, confusion handling |
| `references/learn-by-rebuilding.md` | Learn by rebuilding from scratch; pick free APIs; autopsy dead projects |

## References inside job-search

| File | What it covers |
|---|---|
| `references/pipeline.md` | The application pipeline — profile, fit scoring, drafter-reviewer loop, ATS check, outcome tracking |
| `references/discovery-jobspy.md` | Job discovery — board search into a table/CSV, search-only rules, rate and ToS limits |
| `references/interview-prep.md` | Interview prep — mocks, OA sims, system design, HR rounds, resume roasts, company briefs, prep plans, honesty rules |
| `references/verify-submission.md` | Submission verification — open-posting check, upload check, confirmation capture, follow-up mail classification |
| `references/salary-negotiation.md` | Salary negotiation — market data, the three numbers, scripts, counter-offer traps |
| `references/contracts-proposals.md` | Contracts and proposals — clauses, jurisdiction notes, templates, DOCX conversion |

## References inside lead-gen

| File | What it covers |
|---|---|
| `references/first-customer.md` | First-customer finding — public-signal research, qualification framework, report shape |
| `references/scout.md` | Social-platform leads — 8 platforms, enrichment, 0–100 scoring, CSV export |
| `references/maps-scraper.md` | Local-business leads from Maps — queries, depth, filters, rate limits, scraped-data rules |
| `references/yc-outreach.md` | Founder outreach lists — batch search, guess labels, verify-first, draft-only |
| `references/freelance-practice.md` | Freelance practice — positioning, pricing, pipeline, contracts, scope creep |
| `references/email-verify.md` | Email checks — verdicts, SMTP limits stated honestly, deliverability routing |
| `references/web-research-ops.md` | Web research operations — routing a research question, site-to-API, read-only browser checks |

## References inside video-craft

| File | What it covers |
|---|---|
| `references/stickman-director.md` | Stickman videos — director vs autopilot, 5-stage story engine, style catalog, voice continuity |
| `references/hypit.md` | Hypit — directed generated-media video, component authoring, voice continuity |
| `references/lapoz-reels.md` | Premium talking-head reels — four templates, word-level karaoke captions, render + verify |
| `references/hyperframes.md` | HTML-to-video — composition contract, registry-first, lint + check gates, deterministic render |
| `references/openmontage.md` | Full-pipeline production — pipeline-first, capability envelope, zero-key path, runtime choice |
| `references/watch-voice-audio.md` | Watch a video + voiceover — engines, transcript limits, voice generation, sample-rate gate |
| `references/code-graphics.md` | Code-drawn graphics — Manim scenes, isometric SVG explainer method, fetching source media |

## References inside linkedin-craft

| File | What it covers |
|---|---|
| `references/post-writing.md` | Post writing — hook formulas, post structure, hook extraction |
| `references/comments-replies.md` | Comments and replies — drafting, thread sweeps, thread monitoring, engager analytics |
| `references/profile-and-planning.md` | Profile optimiser + content planner — pillars, founder angles, weekly plans |
| `references/repurpose-advocacy.md` | Repurposing + advocacy + interviewer — cross-platform adaptation, team advocacy, story bank |
| `references/humanizer-audit.md` | Humanizer audit — AI-tell removal, emoji density, detector audit, pre-publish review |

## References inside multi-agent-team

| File | What it covers |
|---|---|
| `references/team-roles.md` | All 8 roles — job, inputs, outputs, done-criteria, skill routes |
| `references/research-gate.md` | Research note format, review lenses, unanimous pass, 2-round cap |
| `references/plan-format.md` | Human plan template, [P] markers, frozen-plan rule, change protocol |
| `references/execution-loop.md` | Dispatch pattern, brief structure, shared ledger, fix loop cap |
| `references/handoff-protocol.md` | Shared board, message format, Master-only-to-owner rule, escalation |
| `references/test-gate.md` | Verifier independence, production-style checks, evidence standard |
| `references/reference-rebuild.md` | Reference extraction, rebuild, side-by-side diff, zero-diff rule |
| `references/continuous-ops.md` | Schedules, shared queue, per-run reports, honest limits |

## Principles
- **Complete, not partial.** Every check runs. N/A only with evidence the mechanism doesn't exist.
- **Evidence, not claims.** A check passes only on observed behaviour (live probe or test output).
- **Gate, not report.** Deploy is blocked until the gate passes.
- **Minimal fixes.** Smallest complete change, server-side, verified by an independent agent.
- **Human vs agent split.** What only a human can do is listed as open, never hidden.
- **Graph first.** Build the project graph before reading code; update it after changes. Never read the whole codebase.

## Provenance
Built from the 85-check pre-launch audit (Mayank Shah v2.0), OWASP Top 10 (2025 + LLM), the Cloudflare 6-phase audit workflow, viral pre-launch checklists, SkillOpt (Microsoft) for skill evolution, GitHub Spec Kit (github/spec-kit, MIT) for spec-kit, and the Strix pentest skill family (Apache-2.0, summarised tool-generically) plus OWASP Top 10:2025 / API Security Top 10 (2023) for pentest. Batch 2 (19 Nov 2026): `seo` from 28 sources (MIT, AgriciDaniel; FLOW prompts CC BY 4.0), `instagram-craft` from 13 and `youtube-craft` from 11 (no license files in source dirs; scripts/data copied as functional assets), `coding-craft` from 24, `ship-workflow` from 23, `codebase-intelligence` from 9, `job-search` from 7, `lead-gen` from 11, `video-craft` from 11 (openmontage AGPLv3 and ghost-downloader GPLv3 method/usage only, no code), `linkedin-craft` from the linkedin-skills bundle (MIT, distilled, draft-only) — all distilled in own words; pilots gated PASS per skill-evolution (every new skill 4/4 validation). `multi-agent-team` (20th skill, 19 Nov 2026): distilled in own words from dispatching-parallel-agents, executing-plans, brainstorming, verification-before-completion, elephant-goldfish-model, advisor-orchestrator-worker, agency-agents (roles only); routes to the other Rkhshak skills instead of re-teaching them; pilot gated PASS (train 8/8, validation 4/4 vs baseline 2/8 and 0/4), shipped v1 as-is, no edit.
