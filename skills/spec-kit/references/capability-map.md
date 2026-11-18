# Capability map (Phase 0)

Most requests describe one capability. If this one does, skip this step entirely and go straight to Specify — Phase 0 exists for the exception, not the rule.

## When to run it

Decompose before specifying when a single requirement bundles several independently testable capabilities:

- It names distinct capabilities with their own consumers or data (e.g. identity, billing, notifications, reporting).
- Acceptance criteria cluster into groups that could ship and be verified separately.
- One capability could be cut or replaced without rewriting the others' requirements.

## The map

Small and reviewable — a module table plus a build order, not a project plan:

```markdown
# Capability Map: [Initiative Name]

| Module id | Responsibility | Depends on |
|---|---|---|
| identity | Accounts, sessions, sign-in | — |
| billing | Plans, invoices, payments | identity |
| notifications | Email and webhook fan-out | identity |
| reporting | Usage dashboards | billing, notifications |

Build order: identity → billing, notifications → reporting
```

Rules:

- **Stable module ids.** Kebab-case, chosen once, never renamed mid-initiative. Specs, plans, and tasks select work by these ids instead of guessing which spec is active.
- **Dependency direction, no cycles.** Arrows point one way. If two modules each need the other, they are one module.
- **Interfaces live at the boundary.** The map records that `billing` depends on `identity`; the contract between them belongs in the provider module's spec.

## Gate and recursion

- The map is gated like every phase: the human reviews module boundaries, dependency direction, and build order before any module spec is written. Getting the map wrong is expensive; reviewing ten lines is not.
- Then recurse per module, in dependency order: Specify → Plan → Tasks → Implement for each module. Each module gets its own spec, scoped to that module's objective, boundaries, and success criteria.
- Save the approved map at the project root and each module's spec alongside it, named by module id (`SPEC-identity.md`, `SPEC-billing.md`) — the map, not filename guessing, is the index of what exists.

## Red flags

- One spec whose requirements span several independently testable capabilities.
- Module boundaries or build order decided implicitly during implementation because no capability map was approved up front.
- Decomposing during planning instead: planning slices tasks within a spec. By then the oversized artifact already exists — boundaries must be decided before the spec is written, not after.
