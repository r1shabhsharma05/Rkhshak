# Context Packing — load only what the task needs

Distilled from the context-engineering skill (MIT). Method in our own words; the full hierarchy and strategies live in that source. Use when starting a new session, when output quality degrades, when switching tasks, or when setting up rules files for a project.

## The context hierarchy (load in this order)
1. **Rules files.** The project's standing rules: stack, commands, conventions, boundaries, patterns. These govern everything below.
2. **Specs and architecture.** The plan, the design, the module map — what the task is and how the system is shaped.
3. **Relevant source files.** Only the files the task touches, pointed to by the graph or the plan. Never the whole codebase.
4. **Error output.** The actual failure: test output, build log, stack trace. Read it, do not summarize it from memory.
5. **Conversation management.** Summaries of earlier turns when the session is long; the summary replaces the raw history, it does not sit beside it.

## Context packing strategies
- **The brain dump.** When the task is unclear: dump everything known, then cut to what matters. A starting move, not a final state.
- **The selective include.** When the task is clear: include only the files, rules, and specs the task names. Default to this.
- **The hierarchical summary.** When the session is long: a project map (module → purpose → key files) plus the current task state, replacing raw history.

## Context budget management
- **What to cut first:** raw conversation history, then full file contents (keep the map + the touched ranges), then background reading.
- **What to protect until the end:** the rules files, the current task's spec, the failing output, the decision log.
- **Compress before dropping.** Summarize a file before removing it; never drop the only copy of a decision.
- **Order for recency.** The most recent task state and the freshest error output go last, closest to the work.

## Confusion management
- **When context conflicts:** the rules file wins over conversation memory; the spec wins over a stale summary; the newest error output wins over an older one. State the conflict and which source won.
- **When requirements are incomplete:** ask for the missing piece once, with the live status attached — do not re-ask the whole queue.
- **Inline planning pattern.** When a task grows mid-session: stop, write the plan down (tasks + order + checkpoints), then resume. A plan in the head is not a plan.

## Anti-patterns
- Loading the whole repo "just in case" — the graph exists so you do not have to.
- Keeping every turn verbatim in a long session — summarize, then drop.
- Treating a stale summary as current — re-check it against the live state before acting.
