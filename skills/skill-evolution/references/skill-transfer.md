# Skill Transfer — what survives a move, and how to prove a win

A trained skill is a text document. It can move. The question is whether it still works after the move — and whether you can prove it got better, instead of just feeling better.

## Transfer (what moves, what doesn't)
- **Across model scales.** An optimized skill transfers across model sizes without further optimization. A skill trained on a strong model usually still helps a smaller one; test it, don't assume it.
- **Between harnesses.** A skill trained inside one agent loop (e.g. Codex) transfers to another (e.g. Claude Code) without re-optimization. The skill is text; the harness is plumbing.
- **To nearby benchmarks.** A skill trained on one task family transfers to a nearby one (same shape, different content). Far jumps (QA → embodied AI) need retraining.
- **When to re-optimize.** New model family, new task type, or a skill that went flat on the new target. Re-optimization starts from the transferred skill (not from scratch) and runs the same loop with the same gate.

## Honest scope (when training works, when it doesn't)
- **Works where tasks recur and have a checkable signal.** The loop needs repetition (the same kind of task, again and again) and a judge that can say pass/fail. Recurring tasks + a real check = training works.
- **Flat on saturated or noisy benchmarks.** If the model is already near the ceiling, or the judge is noisy, the gain is flat within run-to-run noise (about ±1–2 points). A sub-1.5-point difference is noise, not improvement. The gate keeps the worst case bounded — it just won't find a win where there is none.
- **Never report a noisy gain as a win.** If the improvement is inside the noise band, say "no measurable improvement". A small number with a big claim is worse than no number.

## Proving "B beats A" (the A/B evalkit)
A single run never proves one skill beats another. Use the paired evalkit:
1. **One fixed task manifest.** Both conditions (A and B) run on the exact same tasks. Different tasks, different difficulty — the comparison is void.
2. **McNemar's test.** A paired statistical test on the same tasks — it asks whether B wins more often than A on the tasks where they differ, not just whether the averages differ.
3. **Bootstrap CI on the success-rate delta.** Report the confidence interval, not just the point estimate. A delta of +3 with a CI of (−1, +7) is "no proven win".
4. **A/A check first.** Run A against A. If the evalkit reports a difference, the harness is broken — fix it before comparing A vs B.
- **The nightly gate is unchanged.** The evalkit proves a claim; the gate decides what ships. A proven win still goes through the gate before it lands.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Transfer tested on the new model/harness/benchmark | "It should transfer" with no measurement |
| 2 | Re-optimization starts from the transferred skill, not scratch | Retraining from zero after a transfer |
| 3 | Training claimed only where tasks recur + signal is checkable | A "trained" skill on one-off tasks with no judge |
| 4 | Sub-noise gains reported as "no measurable improvement" | A +1-point gain claimed as a win |
| 5 | "B beats A" proven on one fixed manifest + McNemar + bootstrap CI | A single-run comparison quoted as proof |
| 6 | A/A check run before any A/B comparison | A comparison from an unverified harness |
