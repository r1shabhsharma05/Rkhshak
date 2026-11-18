# API and Interface Design — contracts that survive users

Distilled from two sources, in our own words: api-and-interface-design (MIT) and codebase-design. Full patterns live in those sources. Use when designing APIs, module boundaries, or any public interface.

## Core principles
- **Contract first.** Define the interface — its shapes, its errors, its guarantees — before implementing it. The contract is reviewed before the code.
- **Hyrum's law.** With enough users, every observable behaviour becomes a dependency. Assume anything observable will be relied on; do not change observable behaviour casually.
- **The one-version rule.** One supported version of an interface at a time where possible; versioning is a cost, not a feature.
- **Consistent error semantics.** Same failure, same shape, same status, everywhere. Errors are part of the contract.
- **Validate at boundaries.** Every input crossing a boundary is validated there, once, with a schema — see `references/api-integration.md`. Never trust caller input inside the implementation.
- **Prefer addition over modification.** Add a new field or endpoint; do not change the meaning of an existing one.
- **Predictable naming.** One name for one concept, everywhere; no synonyms across endpoints.
- **Honour an idempotency key.** Retried requests with the same key must not execute twice.

## REST patterns
- **Resource design:** nouns, not verbs; one resource, one shape; nested resources only where the nesting is real.
- **Pagination:** cursor-based where order matters; always bounded page sizes; the response says whether more pages exist.
- **Filtering:** explicit, documented parameters; unknown parameters rejected or ignored — but the choice is documented, not accidental.
- **Partial updates (PATCH):** update only the fields sent; distinguish "absent" from "null".

## TypeScript interface patterns
- **Discriminated unions for variants.** A tagged union narrows precisely; a bag of optional fields does not.
- **Input/output separation.** The type accepted and the type returned are different types; do not reuse one for both.
- **Branded types for IDs.** An ID type that cannot be confused with a plain string prevents a whole class of mix-ups.

## Deep vs shallow modules (codebase-design)
A deep module does a lot through a narrow interface; a shallow module does little through a wide one. Prefer deep modules: push complexity inside, keep the interface small. Design for testability: a module that cannot be tested in isolation has the wrong seams. When deciding where a seam goes, put it where the interface is stable and the implementations vary.

## Red flags
- An endpoint whose response shape depends on who calls it.
- A breaking change shipped as a minor fix.
- An interface designed by copying the database schema.
