---
name: codebase-intelligence
description: "Understand a codebase before touching it — map it as a queryable graph, trace callers and impact, ground decisions in official docs, read its history, and turn corrections into rules. Use when starting work in an unfamiliar repo, before any edit, when answering 'what depends on this' or 'why is it like this', or when a session's corrections should become lasting rules."
---

# Codebase Intelligence — map first, then act

## Purpose
Most bad edits come from acting on a codebase the agent has not understood: the wrong caller changed, the hidden dependency broken, the documented pattern ignored. This skill makes understanding the first step, not a skipped one. Map the code, read its history, check the official docs, and only then change anything.

Use it when starting work in an unfamiliar repo, before any edit to shared code, when asked what depends on something or why something exists, when choosing a free API or rebuilding a concept to learn it, or when a session produced corrections worth keeping.

## How it works (any user, any project, any stack)
No setup. No config. The agent reads this skill and the references, then understands before acting.

## Workflow
1. **Map the code.** Build or refresh the knowledge graph and answer from it, not from grep — see `references/graphify.md`. For session-by-session learning trails, see `references/trail-code.md`.
2. **Pack the context.** Load only what the task needs, in hierarchy order, inside a budget — see `references/context-packing.md`.
3. **Ground in the source.** Before implementing against a library or framework, fetch its official docs and follow the documented pattern — see `references/source-driven.md`.
4. **Read the history.** When the question is why code exists, dig the commits — see `references/commit-archaeology.md`. When a whole project died, autopsy it before starting its replacement — see `references/learn-by-rebuilding.md`.
5. **Keep the corrections.** Turn the session's corrections into rules with their why — see `references/learn-taste.md`.
6. **Then act.** Hand off to `minimal-code` for the change itself, `coding-craft` for writing and verifying it, `ship-workflow` for planning and landing it.

## References
| File | What it covers |
|---|---|
| `references/graphify.md` | Build/query a codebase knowledge graph — callers, impact, paths, hubs, explanations |
| `references/trail-code.md` | Session learning trails on top of the graph — what was learned, what to re-check |
| `references/source-driven.md` | Ground every decision in official docs — detect stack, fetch, implement, cite |
| `references/commit-archaeology.md` | Reconstruct why code exists from git history, with evidence rules |
| `references/learn-taste.md` | Turn corrections into lasting rules, with their why |
| `references/context-packing.md` | Context hierarchy, packing strategies, budget, confusion handling |
| `references/learn-by-rebuilding.md` | Learn by rebuilding from scratch; pick free APIs; autopsy dead projects |

## Rules
- **Map before editing.** No edit to shared code without first answering: who calls this, what depends on it, what does it call.
- **The graph answers, grep confirms.** A graph query is the answer; reading the file is the check. Never present a grep hit as the whole picture.
- **Docs over memory.** If the official docs and your memory disagree, the docs win. Cite the doc you followed.
- **History is evidence, not gossip.** Every "why" claim needs a commit, a message, or a doc — never a guess about intent.
- **Corrections become rules or they repeat.** A correction with no recorded why will be needed again next session.
- **Read-only by default.** Mapping, tracing, and autopsy change nothing. An edit is a separate step under its own skill.
- **Honest limits.** A graph is only as fresh as its last update; an ambiguous edge is labelled, never silently trusted.

## Provenance
Distilled in our own words from: graphify (Apache-2.0), trail-code (MIT), source-driven-development (MIT), commit-archaeologist (MIT), learn-taste, context-engineering (MIT), build-your-own-x, public-apis (MIT), project-graveyard (MIT). Full method and tooling details live in those sources.
