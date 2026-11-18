---
name: multi-agent-team
description: "Run one owner and a team of specialist agents as a single unit — one command in, research gated by the whole team, a human-readable plan, execution with a test after every step, and nothing ships without the owner's pass. Use when a job needs more than one agent (build a website, research an idea, run daily operations), when a reference must be rebuilt exactly, or when several agents must work together instead of one at a time."
---

# Multi-Agent Team — one command, one team, one pass gate

## Purpose
One person, many agents. An editor handles social media, a job applier
applies daily, an agency owner finds leads, a coder writes code, a
researcher digs deep — and none of them should work in isolation. This
skill puts them all in one place, talking to each other through a shared
board, under one Master who is the only voice the owner hears. One command
starts the team; the research is checked by every agent before any plan
exists; the plan is written so a human understands it at a glance; every
step is tested end-to-end before the next step starts; and nothing ships,
publishes, or posts until the owner passes it.

Use it when a job needs more than one specialist, when a reference
(photo, video, link) must be rebuilt exactly, when an idea must be
researched until it is best in market, or when daily operations
(job applications, lead sweeps, social drafts) must run on a schedule
with a report after each run.

## How it works (any owner, any job, any stack)
No setup. No config. The Master reads this skill and the references,
then runs the loop below. Each role routes to the Rkhshak skill that
already teaches its craft — this skill never re-teaches them:

| Role | Routes to |
|---|---|
| Coder | `coding-craft`, `minimal-code`, `spec-kit`, `design-unslop`, `security-audit` |
| Editor | `instagram-craft`, `youtube-craft`, `video-craft`, `linkedin-craft` |
| Job Applier | `job-search` |
| Agency Owner | `lead-gen`, `seo` |
| Planner | `spec-kit`, `ship-workflow` |
| Verifier | `security-audit` (gate), `coding-craft` (verification) |

## The team
See `references/team-roles.md` for the full definition of each role —
job, inputs, outputs, done-criteria. Summary:

- **Master** — receives the one command, restates it, routes, holds
  every gate, reports to the owner. Only the Master talks to the owner.
- **Researcher** — deep research: scope, goals, market, future,
  viability, risks, best-in-market bar.
- **Planner** — turns approved research into a human-readable plan.
- **Coder** — writes code per the plan.
- **Editor** — social and video work.
- **Job Applier** — daily job applications under hard stops.
- **Agency Owner** — leads and agency pipeline.
- **Verifier** — a separate agent, never the builder; tests end-to-end
  after each step and holds the final gate.

## Workflow — the loop, in order, no step skipped
1. **Intake.** One command in. Master restates goal + scope +
   done-criteria back in one line, routes to the Researcher. Ambiguity
   → ask the owner once, never guess. See `references/handoff-protocol.md`.
2. **Research.** Researcher goes deep — multiple angles, sources,
   competitors, future — and posts a research note to the shared board
   for all agents. See `references/research-gate.md`.
3. **Research gate.** Every agent reviews against its own lens
   (Coder: buildable? Editor: shippable? Agency: sellable? Verifier:
   testable?). PASS only on unanimous pass; otherwise one round of
   deeper research with named gaps. Cap: 2 research rounds, then the
   Master escalates to the owner with the open questions. Never loop
   forever.
4. **Plan.** Planner writes the step-by-step human plan (goal → steps →
   owner → done-criteria → test). Team reviews once. Plan is frozen;
   changes go through the Master as a new step, never silent edits.
   See `references/plan-format.md`.
5. **Execute.** Each agent does its own step in order. Parallel only
   where the plan marks `[P]` — independent, no shared state.
   See `references/execution-loop.md`.
6. **Test after each step.** Verifier runs end-to-end checks
   production-style (build, run, real behaviour, no mocks-as-proof)
   before the next step starts. A failed step goes back to its owner
   with the failing evidence; fix loop capped at 5 rounds, then
   escalate to the owner. See `references/test-gate.md`.
7. **Reference rebuild (only when the owner gives a photo, video, or
   link).** Extract the exact structure, layout, and content from the
   reference, rebuild it, then run a side-by-side diff check (layout,
   copy, colours, spacing, behaviour). Report the measured diff list;
   fix until the diff is zero or each remaining diff is named with its
   cause. Never claim "exact, no diff" without the diff check.
   See `references/reference-rebuild.md`.
8. **Show + owner's pass.** After the final test, the Master shows the
   owner the result + test evidence. Nothing ships, publishes, or
   posts without the owner's explicit pass. The pass is the ship gate;
   "change X" is a new step, not a rework of history.
9. **Continuous ops.** Daily jobs, lead sweeps, social drafts run on
   the owner's approved schedule, each reporting outcome + evidence.
   See `references/continuous-ops.md`.

## References
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

## Rules (strict — follow every one)
- **Only the Master talks to the owner.** Workers talk through the
  shared board, never DM the owner directly. A worker that needs the
  owner escalates to the Master, who asks once.
- **No plan, no build.** Research passes the gate first, then the plan
  is written, then code starts. A step that feels too large to start
  is a step that has not been planned.
- **Unanimous pass or deeper research.** One agent's objection is a
  failed gate, not a minority opinion. The gap is named, the research
  goes one round deeper, and the cap is 2 rounds.
- **The plan is frozen once the team reviews it.** A change is a new
  step added by the Master, with its own owner and done-criteria —
  never a silent edit to a step already in flight.
- **Parallel only when independent.** Shared state means sequential.
  Two agents in one file is a merge conflict, not parallelism.
- **The builder never verifies its own work.** The Verifier is a
  separate agent. A step passes only on the Verifier's observed
  evidence, never on the builder's report.
- **Evidence, not claims.** A check passes only on observed behaviour
  (live probe or test output). "Should work", "looks right", and
  "probably fine" are not evidence. No completion claim without fresh
  verification run in this turn.
- **A failed step returns with its evidence.** The fix loop is capped
  at 5 rounds; after that the Master escalates to the owner with the
  failing evidence and the options. Never loop forever, never hide a
  failure by retrying silently.
- **The owner's pass is the ship gate.** Build, test, and show — then
  stop. Nothing ships, publishes, posts, submits, or pays without the
  owner's explicit pass on that specific result.
- **Never misrepresent LLM use. Never invent numbers, testimonials,
  pricing, or facts.** A number with no source is a guess, and a guess
  is reported as a guess or not at all.
- **Building ≠ deploy.** A green build is not a deploy decision. Deploy
  and publish need the owner's explicit word, separately, each time.

## Hard stops (bind this skill — they are not optional)
- Social posting: draft and schedule only on the owner's word. No
  auto-posting to any channel. LinkedIn: the owner posts himself.
  WhatsApp: always manual, from the owner's own number.
- Job applications: only under the immediate-apply rule with its hard
  stops — no invented answers, no false enrollment, no invented
  passwords, one-time codes only from the owner.
- No submission, payment, or application is ever claimed complete
  without a real confirmation (receipt, confirmation page, reference
  number).
- No secret is ever pasted into chat, a file, a URL, or a repo. Secrets
  go through the secure vault only.
- Security audit before any production deploy or launch
  (`security-audit`); smallest complete fix, server-side,
  evidence-verified (`security-fix`); design-unslop for any UI;
  code-humanizer (no AI tells, WHY comments only); minimal-code
  (delete first, library first, no speculation — ponytail FULL);
  modern-web-guidance for all code work.

## Honest limits
- **Agents run on demand + schedule, not 24/7 unsupervised.**
  "Continuously working" means scheduled runs and a shared queue, each
  reporting outcome + evidence. No agent runs forever without the
  owner, and no run is claimed that did not happen.
- **"Exact same as the reference" is a measured claim, not a feeling.**
  It is true only after the side-by-side diff check in
  `references/reference-rebuild.md` reports zero diffs. Until then it
  is "N diffs remaining", listed by name.
- **"Best in market" is a research verdict, not a slogan.** It means
  the research note names the competitors, the bar, and the evidence —
  and the whole team passed it. If the research cannot name the bar,
  the claim is not made.
- **One command starts the team; it does not finish the job.** The
  owner still passes each result. The team does the work; the owner
  keeps the decisions.

## Provenance
Distilled in our own words from: dispatching-parallel-agents (MIT) and
executing-plans (MIT) for dispatch, briefs, the task loop, and the fix
loop; brainstorming (MIT) and idea-refine for shaping the idea;
verification-before-completion for the evidence-before-claims gate;
elephant-goldfish-model (Apache 2.0) for fresh-context review and the
fail-closed rule; advisor-orchestrator-worker (Apache 2.0) for the
orchestrator / advisor / worker tiers, budget, and escalation; and
agency-agents (MIT) for the specialist-roster idea — roles only, the
268-file roster is distilled, not copied. Routes to, never duplicates:
`spec-kit`, `ship-workflow`, `codebase-intelligence`, `coding-craft`,
`minimal-code`, `design-unslop`, `security-audit`, `job-search`,
`lead-gen`, `instagram-craft`, `youtube-craft`, `video-craft`,
`linkedin-craft`, `seo`.
