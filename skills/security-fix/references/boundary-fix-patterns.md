# Boundary Fix Patterns — schema validation, uploads, destructive paths, model output, data

Extra fix patterns for vulnerability classes that `references/fix-patterns.md` does not cover. Same rule applies: copy the pattern, adapt only the names, smallest complete change, server-side, verified by evidence.

## Schema validation at boundaries

Validate at the boundary with a schema — allowlisted shape, lengths, enums, formats — and reject with a structured error. Downstream code uses only the parsed, typed value, never the raw input.

```js
// BAD: raw input flows straight into logic
const limit = req.query.limit; // attacker-controlled string

// GOOD: parse once at the boundary, use only the parsed value
const parsed = LimitSchema.safeParse(req.query);
if (!parsed.success) return res.status(422).json({ error: "invalid input" });
const limit = parsed.data.limit; // typed, bounded number
```

## File upload safety

Allowlist content types, cap size, verify content (magic bytes) when it matters. The extension proves nothing — check what the bytes actually are, store outside the web root, and serve with a safe content type, never the uploaded one.

```js
// BAD: trust the extension, store where it can be served as code
// GOOD: allowlist type + size cap + magic-byte check + random stored name
const ALLOWED = new Set(["image/png", "image/jpeg"]);
if (!ALLOWED.has(file.mimetype) || file.size > 5 * 1024 * 1024) reject();
if (!startsWithMagicBytes(file.buffer, PNG_MAGIC)) reject();
await store(randomName() + ".bin", file.buffer); // never the user-supplied name
```

## Destructive operations on derived paths

A delete, move, or overwrite whose target comes from a payload, a config value, or another process's command line is only safe when all three hold: the resolved target (symlinks resolved) sits under an **allowlisted root**; it is at least one level **below** that root; and it carries **ownership evidence read before the operation**. A shape check on the path is not authorization.

```js
// BAD: shape check only — "../" and symlinks escape it
if (!/^[\w.-]+$/.test(name)) reject();
await fs.rm(path.join(BASE, name), { recursive: true });

// GOOD: resolve symlinks, then check root + depth + ownership
const target = await fs.realpath(path.join(BASE, name));
if (!target.startsWith(BASE + "/")) reject();          // under the allowlisted root
if (target === BASE || path.dirname(target) === BASE) reject(); // at least one level below
if (!(await ownedByCurrentUser(target))) reject();      // ownership read before the call
await fs.rm(target);
```

On refusal, log the rejected target and stop; never fall back to a broader default path.

## Model / LLM output handling

Model output is untrusted input. Never pass it into `eval`, SQL, a shell, raw HTML, or a file path. Parse defensively, validate against a schema, then encode — exactly as with any other untrusted input.

```js
// BAD: model text straight into a query / the DOM
await db.query(`SELECT * FROM docs WHERE title = '${modelText}'`);
el.innerHTML = modelText;

// GOOD: validate against a schema, then use a parameterized query / encoded output
const parsed = DocSchema.safeParse(JSON.parse(modelText));
if (!parsed.success) reject();
const row = await db.query("SELECT * FROM docs WHERE title = $1", [parsed.data.title]);
el.textContent = parsed.data.summary; // encoded, never raw HTML
```

Also: keep secrets, other tenants' data, and the full system prompt out of the model context; scope tool permissions; validate every tool argument; confirm destructive actions before running them.

## Data minimization (privacy fix)

The cheapest data to protect is the data never collected. When a fix touches personal data: classify the field, collect only against a stated purpose, set a retention limit, and make sure the deletion path reaches backups, caches, and analytics copies — not just the live row. A "delete my account" that only flips a flag is not a fix.

## How to use this file

Open the section you need when you reach that code, not before. Each pattern is one concrete implementation of the rule — adapt names only. If no pattern fits the finding, say so; don't invent one.

## Provenance

Summarised in our own words from the security-and-hardening patterns (schema validation, file uploads, destructive paths, LLM output handling, data classification).
