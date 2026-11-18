# Specify

Turn a natural-language feature description into a structured specification at `specs/NNN-name/spec.md` (next sequential 3-digit number, or a timestamp prefix where the project uses one). One feature per invocation. The spec directory name and the git branch name are independent.

## The core rule

**Focus on WHAT users need and WHY. Avoid HOW to implement** — no tech stack, no APIs, no code structure. Written for business stakeholders, not developers. A spec that names the implementation is not a spec.

## Execution flow

1. **Short name.** 2–4 words, action-noun format where possible (`user-auth`, `analytics-dashboard`). Preserve technical terms and acronyms.
2. **Create the directory and spec file** from the spec template; record the resolved directory so later steps can find it without guessing from branch names.
3. **Load the constitution** (`.specify/memory/constitution.md`) if it exists — its principles constrain the spec.
4. **Parse the description.** Extract actors, actions, data, constraints.
5. **Ambiguities:** make informed guesses from context and industry standards, and document them as assumptions. Mark with `[NEEDS CLARIFICATION: specific question]` **only** when the choice significantly impacts scope or user experience, multiple reasonable interpretations exist with different implications, or no reasonable default exists. **Maximum 3 markers total**, prioritized by impact: scope > security/privacy > user experience > technical details.
6. **User scenarios & testing.** If no clear user flow can be determined, stop — do not invent one.
7. **Functional requirements.** Each requirement must be testable.
8. **Success criteria.** Measurable, technology-agnostic outcomes — quantitative (time, volume, rate) and qualitative (task completion, user satisfaction). Verifiable without implementation details. Good: "Users can complete checkout in under 3 minutes". Bad: "API response time is under 200ms" (too technical), "Redis cache hit rate above 80%" (technology-specific).
9. **Key entities**, if data is involved.

## Spec template

```markdown
# Spec: [Feature Name]

## Objective
[What we're building and why. Who is the user? What does success look like?]

## User Scenarios & Testing
[Primary flows, acceptance scenarios, edge cases]

## Functional Requirements
[Each testable: FR-001, FR-002, ...]

## Success Criteria
[Measurable, technology-agnostic outcomes]

## Key Entities
[Data involved: name, fields, relationships — only if applicable]

## Assumptions
[Reasonable defaults used where the request was silent]

## Open Questions
[Anything unresolved — the [NEEDS CLARIFICATION] markers live here too]

## Boundaries
- Always: [e.g. run tests before commits, validate inputs]
- Ask first: [e.g. schema changes, adding dependencies, CI changes]
- Never: [e.g. commit secrets, remove failing tests without approval]
```

Sections that don't apply are removed entirely, never left as "N/A". Mandatory sections are completed for every feature.

## Assumptions, stated up front

Before writing spec content, list what is being assumed — assumptions are the most dangerous form of misunderstanding, and surfacing them is the spec's entire purpose:

```
ASSUMPTIONS I'M MAKING:
1. This is a web application (not native mobile)
2. Authentication uses session-based cookies (not JWT)
→ Correct me now or I'll proceed with these.
```

Reframe vague requirements as success criteria and confirm them: "Make the dashboard faster" becomes "Dashboard loads in under 2.5s on a 4G connection; initial data load completes in under 500ms; no layout shift during load" — then ask whether those are the right targets.

## Spec quality checklist

After writing the spec, create `specs/NNN-name/checklists/requirements.md` and validate against it:

- [ ] No implementation details (languages, frameworks, APIs)
- [ ] Focused on user value and business needs
- [ ] Written for non-technical stakeholders
- [ ] All mandatory sections completed
- [ ] No `[NEEDS CLARIFICATION]` markers remain
- [ ] Requirements are testable and unambiguous
- [ ] Success criteria are measurable and technology-agnostic
- [ ] All acceptance scenarios are defined
- [ ] Edge cases are identified
- [ ] Scope is clearly bounded
- [ ] Dependencies and assumptions identified

If items fail (other than unresolved markers): list them, fix the spec, re-validate — at most 3 iterations, then document what remains and warn the user. If markers remain: present at most 3 questions with suggested answers (options table + implications), wait for the user's choices, replace each marker with the answer, and re-validate.

## Stop here (critical)

Once the spec is saved: summarize it, list open questions, ask the human to approve it or request changes, and **stop the turn immediately**. Do not start planning, and do not write code, in this turn. Planning starts only after approval in a later turn.

## Rationalizations to reject

| Rationalization | Reality |
|---|---|
| "This is simple, I don't need a spec" | Simple tasks don't need *long* specs, but they still need acceptance criteria. A two-line spec is fine. |
| "I'll write the spec after I code it" | That's documentation, not specification. The spec's value is forcing clarity *before* code. |
| "The spec will slow us down" | A 15-minute spec prevents hours of rework. |
| "Requirements will change anyway" | That's why the spec is a living document — update it when decisions change, when scope changes, and reference it in the change that implements it. |
| "The user knows what they want" | Even clear requests have implicit assumptions. The spec surfaces them. |
