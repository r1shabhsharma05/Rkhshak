# Docs and Decisions — write it down, then check it reads

Distilled from three sources, in our own words: documentation-and-adrs (MIT), first-reader (MIT) and its `interview.md`, `personas.md`, `report.md`, `room.md` references, and teach (MIT). Full templates live in those sources. Use when documenting a decision, changing a public API, shipping a feature, or drafting anything a stranger must understand.

## Architecture Decision Records (ADRs)
Write an ADR when a decision is hard to reverse, affects many files, or will be questioned later. Match the existing convention first (location, numbering, format); if none exists, start one.
- **Template:** context (what forced the decision), decision (what was chosen), alternatives considered (each with why it lost), consequences (good and bad, stated honestly).
- **Lifecycle:** proposed → accepted → superseded (never deleted — a superseded ADR is history, and history explains the code).
- One decision per ADR. An ADR that decides three things will be wrong about one of them.

## Inline documentation
- **Comment when:** the why is not obvious from the code; a workaround exists for a real bug (name the bug); a gotcha will bite the next reader.
- **Do not comment when:** the code already says it; the comment restates the code; the comment describes what the code does instead of why.
- **Document known gotchas** where they will be found — next to the code, not in a distant wiki.

## API documentation
- **Inline with types** (preferred for TypeScript): the type and its doc comment are the documentation; keep them honest.
- **OpenAPI / Swagger for REST APIs:** the spec is generated from the code or the code from the spec — never a hand-written spec that drifts from both.

## README structure
Quick start, commands, architecture (a map, not an essay), contributing, and a changelog. A README that does not say how to run the thing has failed its first job. Update the README in the same change as the behaviour it describes.

## Changelog maintenance
One entry per release: added, fixed, changed — written for humans, with the user-visible effect, not the commit hash. A changelog entry that only a developer understands is a commit message in the wrong file.

## Documentation for agents
Rules files, command lists, and conventions live where an agent will read them (the repo root or the docs folder), in plain language, with no assumed context. If an agent needs a fact, it should be written down, not remembered.

## First-reader check (before shipping a draft)
Simulate how a real reader experiences the draft, moment by moment — do not read it as its author:
1. **Scope and genre:** who is this for, and what kind of document is it?
2. **Cast the reader:** pick a realistic reader (not an expert, not a beginner — the actual audience).
3. **The skim gate:** can the reader get the point from headings and first lines alone? If not, the structure is wrong.
4. **The timed reads:** read it at a realistic pace, noting where attention drops, where it confuses, where it quits.
5. **The recall test:** after reading, what does the reader remember? If the main point is not recalled, it was not communicated.
6. **The trust ledger:** every claim the draft makes, and whether the reader has reason to believe it. Unproven claims cost trust.
7. **Your own read, then the report:** only after the simulated reads, read it as the author and write the report — what to fix, in order, with the exact passages.

## Teach-back (teach)
When explaining something built or learned: teach it back in plain language, at the learner's level, with a concrete example and a check ("what would you do if …?"). Fluency (can explain it) matters more than storage (can recite it). If the explanation needs jargon the learner does not have, the explanation is not ready.
