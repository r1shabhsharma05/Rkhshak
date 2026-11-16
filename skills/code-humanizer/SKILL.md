---
name: code-humanizer
description: "Write code that reads like a human wrote it - remove AI tells, use human style, keep it natural."
---

# Code Humanizer

## Purpose
AI-written code has tells. A reviewer can spot it in seconds: verbose comments explaining obvious things, perfect uniform structure, generic names, over-abstraction, defensive code everywhere. This skill makes code read like a human developer wrote it — not by faking mistakes, but by writing the way humans actually write: pragmatic, specific, and opinionated.

Use it when writing new code, and when rewriting AI-generated code so it passes review without anyone asking "did AI write this?"

## When to use it
- Writing new code that will be reviewed by humans (PRs, client work, open source).
- Cleaning up AI-generated code before it ships.
- Any time the code needs to look like it came from a person, not a generator.

## How it works (any user, any project, any stack)
No setup. No config. The agent reads this skill and the references, then writes or rewrites code in human style.

## Multi-agent
Works with Claude, Codex, and any agent that reads SKILL.md. The rules are written as plain checks, not model-specific tricks.

## Workflow
1. **Read the code (or the task).** If rewriting existing code, read it first. If writing new code, understand the task and the codebase's existing style.
2. **Match the codebase.** Human code fits its neighbours. Read the files around the change — match their naming, their comment density, their structure. A human writing in an existing codebase copies the local style, not a textbook.
3. **Check the tells.** Run every line against `references/ai-tells.md`. Remove every tell: verbose comments, generic names, over-abstraction, defensive bloat, perfect structure.
4. **Check the prose.** Code has prose in it — comments, docs, commit messages, READMEs, error messages, UI copy. Run all of it against the 26 patterns in `references/prose-tells.md` (from blader/humanizer, MIT): not-X-but-Y, one-line closers, staged run-ups, forced triads, inflated claims, sales language, stock AI words, chatbot residue. Mark the tells strongest first, draft the rewrite keeping every claim, check the draft, then write the final version. If the user gives a writing sample, match its voice — the sample overrides the patterns.
5. **Write in human style.** Follow `references/human-style.md`: comments explain WHY (only where the why isn't obvious), names are domain-specific, small pragmatic trade-offs are fine, the code has a point of view.
6. **Read it aloud.** Read the code as if explaining it to a colleague. If it sounds like documentation, rewrite it. If a sentence in a comment sounds like a tutorial, delete it.
6. **Verify.** The check is simple: would a senior developer accept this in review without asking whether AI wrote it? If the answer is no, find the tell and remove it. Never fake human mistakes (typos, bugs, sloppy formatting) — humans write good code, and faking errors is dishonest.

## Rules
- **Never fake mistakes.** No deliberate typos, no fake bugs, no sloppy formatting to "look human". Human code is good code. The skill removes AI tells, it does not add human flaws.
- **Never lie about authorship.** If asked whether AI wrote the code, answer honestly. This skill is about style, not deception.
- **Comments explain WHY, not WHAT.** If the code says what it does, the comment is redundant. Delete it.
- **Match the codebase, not a textbook.** Local style wins over "best practice" every time.
- **Small and specific beats comprehensive.** A human writes the code the task needs, not the code that might be needed someday.
- **A point of view.** Every piece of code makes visible choices. Hedge nothing. If two approaches exist, pick one and commit.
