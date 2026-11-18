# Trail-Code — session learning on top of the graph

Distilled from the trail-code skill (MIT). Method in our own words; install and MCP details live in that source. Use before deep work in an unfamiliar repo, when a session keeps re-discovering the same facts, or when learnings from one session should survive into the next.

## What it does
A self-learning context layer for coding agents: a code graph (files, functions, callers, built on tree-sitter) plus learnings saved from sessions. The graph answers "what connects to what"; the trail answers "what did we already learn about this".

## Commands (run from the target repo dir, or pass the dir)
- `trail init [dir]` — create the trail for a repo. Only on explicit approval: it writes state into the repo.
- `trail mcp [dir]` — serve the MCP tools: graph queries plus saved learnings.
- Query the graph for callers, callees, and paths the same way as `references/graphify.md`; then check the trail for prior learnings about those nodes before re-deriving them.

## When to use vs graphify
- Graphify is the map: structure, edges, impact. Trail-code is the memory: what past sessions concluded about that structure.
- Use graphify alone for a one-off question. Use trail-code when the work spans sessions and the same areas keep coming up.
- Both are read-first. Neither edits code.

## Rules
- Never initialise a trail without explicit approval — it writes state.
- A saved learning is a claim with a source, not a fact. If the code changed since the learning was saved, re-verify it against the graph before trusting it.
- Record a learning only when it is general (a rule about this codebase, not a note about one line) and only with the evidence that supports it.
