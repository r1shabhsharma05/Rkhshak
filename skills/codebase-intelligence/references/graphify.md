# Graphify — the codebase as a queryable graph

Distilled from the graphify skill (Apache-2.0, Graphify Labs). Method in our own words; install and CLI details live in that source. Use to understand an unfamiliar repo, trace callers and impact before an edit, or answer architecture questions without reading file by file.

## What it does
Parses a folder — code via AST parsing, plus docs, SQL schemas, configs, and PDFs — into a persisted knowledge graph. Every edge carries its source file and line, and is labelled EXTRACTED (read from the code), INFERRED (deduced), or AMBIGUOUS (uncertain). Community detection groups related modules. The graph persists across sessions and updates incrementally; rebuild from scratch after big refactors or deletions.

## Core commands (run from inside the repo, or pass the graph path)
- `graphify update <path>` — build or refresh the graph (AST only, no model needed).
- `graphify query "<question>"` — traverse the graph to answer a question.
- `graphify path "A" "B"` — shortest path between two nodes or concepts.
- `graphify explain "X"` — plain-language explanation of a node plus its neighbours.
- `graphify affected "X"` — reverse impact: everything that depends on X.
- `graphify god-nodes` — most-connected nodes: the architectural hubs.
- `graphify clone <url>` — clone a repo locally, ready to graph.
- `graphify merge-graphs g1.json g2.json` — one cross-repo graph from several.
- `graphify watch <path>` — rebuild automatically on code changes.

## When to use it
- First day in an unfamiliar repo: build the graph, ask it for the main flows, then read only the files it points to.
- Before any edit to shared code: `affected` on the target, `path` between the entry point and the change.
- Architecture questions: `god-nodes` for hubs, `explain` for a subsystem, `query` for "how does X work".
- Never read the whole codebase. The graph is the map; files are visited on demand.

## Limits & honesty
- An INFERRED or AMBIGUOUS edge is a lead, not a fact — confirm it by reading the file before acting on it.
- A stale graph lies: update after refactors, deletions, and renames, or the answers describe code that no longer exists.
- The graph shows structure, not intent. For intent, use `references/commit-archaeology.md`.
- No vector store, no model calls for the build itself: the graph is deterministic parsing, so the same code gives the same graph.
