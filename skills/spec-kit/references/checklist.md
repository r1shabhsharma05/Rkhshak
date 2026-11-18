# Checklist

Checklists are **unit tests for requirements writing** — they validate the quality, clarity, and completeness of requirements in a given domain. If the spec is code written in English, the checklist is its unit test suite.

## What checklists are FOR

- ✅ "Are visual hierarchy requirements defined for all card types?" (completeness)
- ✅ "Is 'prominent display' quantified with specific sizing/positioning?" (clarity)
- ✅ "Are hover state requirements consistent across all interactive elements?" (consistency)
- ✅ "Are accessibility requirements defined for keyboard navigation?" (coverage)
- ✅ "Does the spec define what happens when the logo image fails to load?" (edge cases)

## What checklists are NOT for

- ❌ "Verify the button clicks correctly" — not verification/testing.
- ❌ "Test error handling works" / "Confirm the API returns 200" — not checking whether code matches the spec.
- ❌ Checking whether implementation work is complete.

## Ownership and checkbox lifecycle

- Custom checklists generated here are **reviewer-owned** requirements-quality review artifacts.
- `[x]` means the reviewer determined the requirements-quality criterion is satisfied. It does **not** mean implementation work is complete.
- This step generates or appends checklist items; it **must not** mark generated items `[x]`.
- An agent may assist in evaluating items only when explicitly asked by the reviewer.
- Exception: `checklists/requirements.md` is the built-in spec-quality checklist maintained by specify and clarify — do not treat that exception as applying to custom checklists generated here.

## How to generate one

1. Load the feature's spec (and plan/tasks if they exist) and the domain the user named (e.g. UX, security, accessibility, performance).
2. Write checklist items as questions about the requirements, grouped by category (content quality, requirement completeness, consistency, coverage, edge cases). Each item must be checkable against the spec text alone — no implementation knowledge needed.
3. Save to `checklists/<domain>.md` under the feature directory. Never embed a checklist inside the spec itself.
4. Report the file path and item count. Do not mark anything checked.

## Example structure

```markdown
# Checklist: [Domain] — [Feature Name]

**Purpose**: Validate requirement quality for [domain] before planning
**Feature**: [Link to spec.md]

## Completeness
- [ ] Are [domain] requirements defined for every [element] in scope?

## Clarity
- [ ] Is every qualitative adjective ("prominent", "fast", "intuitive") quantified?

## Consistency
- [ ] Are [domain] requirements the same across all similar elements?

## Edge cases
- [ ] Does the spec define behaviour when [failure condition] occurs?
```
