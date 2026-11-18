# Learn by Rebuilding — build it, pick real APIs, autopsy the dead

Distilled from three sources, in our own words: build-your-own-x, public-apis (MIT), project-graveyard (MIT) and its `causes-of-death.md`. Full guides live in those sources.

## Rebuild it to learn it
Recreating a technology from scratch is the fastest way to understand it: a cache, a shell, a database, a version-control tool, a neural network. Pick one concept, follow a step-by-step guide, and build the smallest working version. The goal is understanding, not a production replacement — the rebuild is a learning exercise, and the real tool stays in use. Use when a concept stays fuzzy after reading about it, or when an interview or a design decision needs first-hand knowledge of how the thing works inside.

## Pick a real free API
When a project needs outside data, check the curated free-API index before building a scraper or paying for a service: weather, finance, geocoding, jobs, health, security, test data, and more, across dozens of categories. Rules:
- Verify live first: the index lists what existed when it was written. Check the API still answers before designing around it.
- Read the auth and rate-limit terms before writing any client code.
- Prefer an official API over scraping. Scraping is the fallback, not the plan.

## Autopsy a dead project
Before starting the replacement for a project that died, autopsy the dead one from its git history:
1. **Run it.** Scan the machine for dead side projects; for each, read its history and its last commits.
2. **Name the cause of death.** Common ones: died at the payments wall, killed by a newer project, finished but never shipped, lost to scope growth, abandoned at the first hard bug. Name it from evidence, not from a feeling.
3. **Write the tombstone report.** What it was, what killed it, what was actually learned, what would have saved it.
4. **The resurrection question.** Is the replacement different in the one way that matters — the cause of death addressed, not just the code rewritten? If not, say so before starting.
5. **Relapse watch.** Name the early warning sign of the same death (same wall, same scope pattern) and check for it at the first checkpoint.
6. **Necromancer mode.** Reviving a dead project is allowed only with its cause of death fixed first; otherwise it is a second funeral.

## Gotchas
- A rebuild teaches the concept; it does not prove the concept is worth using. Keep the two judgments separate.
- An autopsy without the git history is a guess. If the history is gone, say the cause is unknown.
- Never let a dead project's unfinished work silently become the new project's scope.
