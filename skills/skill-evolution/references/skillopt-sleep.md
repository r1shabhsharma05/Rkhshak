# SkillOpt-Sleep — nightly offline self-evolution

Sleep is the training loop applied to your own daily work. While you sleep, the agent reviews your past sessions, replays your recurring tasks, and consolidates what it learns into validated skill updates — staged for you to adopt. It never adopts anything on its own.

## One night
1. **Harvest.** Read local session transcripts (Claude Code / Codex / Copilot / Cursor / Pi / OpenCode). Local and read-only. Nothing is uploaded in this step.
2. **Mine.** Find recurring tasks — the things you asked for more than once, the corrections you kept making, the patterns in your feedback. One-off tasks are not mined; recurrence is the signal.
3. **Replay.** Run the mined tasks again with the current skill, on the configured backend. Score each replay against its check. This is where the evidence comes from.
4. **Consolidate.** Reflect on the replays, propose bounded edits to the skill (and to long-term memory), and run the validation gate on real held-out tasks. Only gated edits survive.
5. **Stage.** The surviving proposal is staged for your review. It sits there until you adopt it — or reject it.
6. **Adopt (you).** Read the staged proposal, then adopt it (`adopt --skill NAME` / `adopt --all-skills`) or leave it. Adoption is a human decision, always.

## The rules
- **Review-then-adopt, always.** Nothing auto-adopts. A staged proposal that nobody reviewed is not an improvement — it's an unread suggestion.
- **Gate stays on.** The same validation gate as training (see `references/validation-gate.md`) governs what ships. A night with no gated improvement stages nothing.
- **Data boundary.** Harvest is local and read-only. A real backend sends truncated session excerpts to your provider for mining, replay, judging, and reflection — review your transcripts before running on sensitive projects. The `mock` backend makes no network calls; use it first.
- **Secrets are redacted, not guaranteed.** Known secret-shaped strings are redacted from harvested text — defense in depth, not a promise. Never run sleep on a project with live secrets in transcripts without reviewing first.
- **Optimizer feedback boundary.** Raw judge evidence (regexes, check expressions, internal labels) stays in the audit log. Reflection consumes only a semantic description ("route recurring requests through the consultation utility") — never the raw check. A rule that imitates the test is not a skill.
- **Token budget.** `max_tokens_per_night` (default 400000) stops a night from starting more model work once spent. Steps that didn't start are listed in the report. A night that stops on budget still advances the harvest checkpoint — its sessions aren't mined again.
- **Fan-out (opt-in).** One independent gated proposal per skill hint mined that night, each derived from that skill's own live `SKILL.md`. Missing or ambiguous skills are skipped and reported, never guessed.
- **Evidence log.** Per-field-truncated prompts/replies land in `evidence.jsonl` — sensitive local data. Set `"evidence_log": false` to disable, and apply a retention policy.

## Commands (CLI)
```bash
skillopt-sleep dry-run     # harvest + mine + replay, report only, stages nothing
skillopt-sleep run         # full nightly cycle; proposal staged for review
skillopt-sleep status      # state + latest staged proposal
skillopt-sleep adopt --skill NAME   # adopt one staged skill
skillopt-sleep schedule    # install a nightly cron entry for this project
```

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Nothing adopted without human review | An auto-adopted proposal |
| 2 | Gate on for every staged proposal | A proposal staged without validation |
| 3 | Harvest local + read-only; real-backend excerpts reviewed first | Transcript content sent to a provider unreviewed |
| 4 | Reflection uses semantic feedback, not raw judge evidence | A rule that copies the test's regex or check |
| 5 | Token budget set; skipped steps listed in the report | A night that silently stopped mid-way |
| 6 | Fan-out proposals each from their own live SKILL.md | A proposal applied to the wrong skill |
