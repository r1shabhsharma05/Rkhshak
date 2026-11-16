---
name: skill-evolution
description: "Improve any agent skill the way you train a neural network — epochs, learning rate, validation gates — without touching model weights. Rollout, reflect, bounded edits, gated acceptance, nightly sleep cycles."
---

# Skill Evolution — train skills like neural networks

## Purpose
Any user, any project, any skill — no ML expertise needed. A skill that keeps failing the same way, or a skill that works but should work better, is trained, not rewritten by hand. The skill document is the trainable state; the model is frozen. Every accepted change is proven better on held-out data.

Based on SkillOpt by Microsoft (MIT, https://github.com/microsoft/SkillOpt) — NeurIPS 2026 Spotlight. Summarized here in our own words; the full method, code, and benchmarks live in that repo.

## How a user runs it
1. Pick the skill to improve and the tasks it must handle. Measure the baseline first — the skill's score on a held-out set, before any training.
2. Run the training loop (below). Each epoch proposes bounded edits; the gate accepts only strict improvement.
3. Ship the best skill. The deployed artifact is a compact skill document — no extra model calls at runtime.
4. Or run the nightly sleep cycle: the agent reviews your past sessions, replays recurring tasks, and stages validated updates for you to adopt.

## Multi-agent roles
- **Trainer.** Runs rollouts (target executes tasks with the skill) and collects scored trajectories. Never proposes edits.
- **Optimizer.** Reads rollouts, proposes bounded edit patches. Never executes tasks, never scores itself.
- **Verifier.** Runs the validation gate on held-out data. Never proposes edits. The optimizer's work is judged by the verifier, never by the optimizer.
- Keep the roles separate. The agent that proposes an edit never verifies it.

## Workflow
1. **Baseline.** Measure the skill on a held-out split before training. No baseline, no training — you can't prove improvement without a "before".
2. **Rollout.** The target executes tasks with the current skill. Collect trajectories + judge scores. See `references/training-loop.md`.
3. **Reflect.** The optimizer reads the scored rollouts and proposes edit patches (add / delete / replace). See `references/training-loop.md`.
4. **Aggregate.** Merge patches from many rollouts into one candidate set. Duplicates collapse; contradictory patches resolve by evidence; true conflicts are dropped.
5. **Select.** Rank patches and clip to the learning-rate budget (max edits per epoch). Over-budget patches wait. See `references/edit-budget.md`.
6. **Update.** Apply the selected patches to the skill document. One update per epoch.
7. **Gate.** Score the updated skill on held-out validation. Ship only on strict improvement; otherwise discard the epoch and buffer the rejected edits. See `references/validation-gate.md`.
8. **Epoch boundary.** Slow update + meta-skill memory. Then repeat — until validation stops improving for two consecutive epochs, then stop.
9. **Ship.** The best skill is the artifact. Compact (typically 300–2,000 tokens), no extra runtime calls.
10. **Sleep (nightly).** Harvest past sessions → mine recurring tasks → replay → consolidate behind the gate → stage for human adoption. See `references/skillopt-sleep.md`. Nothing auto-adopts.
11. **Transfer.** A trained skill moves across model scales, between harnesses, and to nearby benchmarks — test it on the new target, don't assume it. Prove "B beats A" with the paired evalkit, never a single run. See `references/skill-transfer.md`.

## Rules (strict — follow every one)
- **Gate always on.** Every shipped change passes the held-out validation gate. Ungated results are diagnostics, never improvements.
- **Strict improvement only.** Equal is rejected. A tie means the edit added nothing.
- **Bounded edits only.** Add / delete / replace, within the learning-rate budget. No full rewrites passed off as edits.
- **Roles stay separate.** The proposer never verifies its own work.
- **Human adopts.** Sleep proposals are staged for review. Nothing auto-adopts.
- **No split leakage.** Train / validation / test stay disjoint. Leakage voids the run.
- **Honest scope.** Training works where tasks recur and the signal is checkable. Sub-noise gains are reported as "no measurable improvement".
- **Evidence, not claims.** A check passes only on observed scores (validation numbers, gate reports, evalkit output).

## References
| File | What it is |
|---|---|
| `references/training-loop.md` | The 6-stage loop (rollout → reflect → aggregate → select → update → evaluate) + epochs + slow/meta update |
| `references/validation-gate.md` | Held-out gate — strict improvement only, rejected-edit buffer, no-regression mode, split-leakage rules |
| `references/edit-budget.md` | Textual learning rate (max edits), bounded add/delete/replace, LR schedule, slow/meta update |
| `references/skillopt-sleep.md` | Nightly offline self-evolution — harvest → mine → replay → consolidate → stage → adopt (human) |
| `references/skill-transfer.md` | What survives a move (models, harnesses, benchmarks) + honest scope + A/B evalkit (McNemar + bootstrap CI) |
