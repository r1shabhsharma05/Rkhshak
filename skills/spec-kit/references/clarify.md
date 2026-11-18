# Clarify

Runs **before** planning. Goal: detect and reduce ambiguity in the active spec and record the answers directly in the spec file. If the user explicitly skips clarification (e.g. an exploratory spike), proceed — but warn that downstream rework risk increases.

## Scan first

Load the spec and the constitution, then scan for gaps using this taxonomy, marking each category Clear / Partial / Missing:

- **Functional scope & behaviour:** core goals, success criteria, explicit out-of-scope, user roles/personas.
- **Domain & data model:** entities, attributes, relationships, identity/uniqueness, lifecycle/state transitions, volume/scale.
- **Interaction & UX flow:** critical journeys, error/empty/loading states, accessibility or localization notes.
- **Non-functional quality:** performance, scalability, reliability/availability, observability, security & privacy, compliance.
- **Integration & external dependencies:** external services/APIs and failure modes, import/export formats, protocol/versioning.
- **Edge cases & failure handling:** negative scenarios, rate limiting, conflict resolution.
- **Constraints & tradeoffs:** technical constraints, explicit tradeoffs or rejected alternatives.
- **Terminology & consistency:** canonical glossary terms, avoided synonyms.
- **Completion signals:** acceptance-criteria testability, measurable definition of done.
- **Placeholders:** TODO markers, unresolved decisions, ambiguous adjectives ("robust", "intuitive") with no quantification.

## Ask — at most 5, one at a time

- Maximum **5 questions total** across the whole session. Only include questions whose answers materially impact architecture, data modeling, task decomposition, test design, UX behaviour, operational readiness, or compliance. Cover the highest-impact unresolved categories first; never ask two low-impact questions while a high-impact area is unresolved.
- Present **exactly one question at a time**. Never reveal future queued questions in advance.
- Each question is either multiple-choice (2–5 distinct, mutually exclusive options) or a short answer (explicitly constrained: "Answer in <=5 words").
- **Question quality:** lead with `**Question:**` followed by a full interrogative ending in `?` — a topic label or requirement id is not a question. Follow it with one plain-language "Why it matters" sentence. Then a recommendation (multiple-choice: `**Recommended:** Option [X] - <reasoning>` plus an options table; short-answer: `**Suggested:** <answer> - <reasoning>`). The user may reply with a letter, "yes"/"recommended", or their own short answer.
- Stop early when all critical ambiguities are resolved, the user signals completion ("done", "good", "no more"), or 5 questions are reached. If no meaningful ambiguities exist, say so: "No critical ambiguities detected worth formal clarification." and suggest proceeding.
- Never ask about implementation method, tech-stack comparison, or task breakdown — those belong to planning, not clarification. Avoid speculative tech-stack questions unless the absence blocks functional clarity.

## Encode each answer back into the spec

After each accepted answer, immediately:

1. Ensure a `## Clarifications` section exists (just after the highest-level overview section) with a `### Session YYYY-MM-DD` subheading for today.
2. Append `- Q: <question> → A: <final answer>`.
3. Apply the clarification to the right section: functional ambiguity → Functional Requirements; actor distinction → User Stories; data shape → Data Model; non-functional constraint → Success Criteria as a measurable target (convert the vague adjective to a metric); edge case → Edge Cases / Error Handling; terminology conflict → normalize the term across the spec, noting the old term once as `(formerly referred to as "X")`.
4. If the clarification invalidates an earlier statement, **replace** it — leave no obsolete contradictory text.
5. Save the spec file after each integration (atomic overwrite), preserving formatting and heading hierarchy. Only allowed new headings: `## Clarifications`, `### Session YYYY-MM-DD`.

## Validate

- Clarifications session holds exactly one bullet per accepted answer, no duplicates.
- Total asked ≤ 5. No lingering vague placeholders the new answer was meant to resolve. No contradictory earlier statement remains. Terminology consistent.
- If `checklists/requirements.md` exists, re-validate it against the updated spec, toggling only the checkbox markers whose state actually changed, and report before/after pass counts (e.g. "12/16 → 15/16 items passing"), newly passing items, regressions, and items still unchecked.

## Completion report

Number of questions asked & answered, path to the updated spec, sections touched, checklist status, and a coverage summary per category: Resolved / Deferred (over quota, or implementation-level) / Clear / Outstanding (still partial/missing but low impact). If anything is Outstanding or Deferred, recommend whether to proceed to plan or clarify again later.
