# Humanize Existing Code — rewrite AI code to read human

When code already exists (written by AI or by a generator), run this pass. Don't rewrite the logic — rewrite the surface.

## The pass (in order)
1. **Strip the comments.** Delete every comment that restates the code. Delete every docstring on a function whose name already explains it. Delete every tutorial paragraph. Keep only comments that explain WHY — and shorten them to one line.
2. **Rename the generic.** `data` → what it actually is. `result` → what it actually is. `handler` → the action (`sendInvoice`). `utils` → split it or name it by what it does. `processData` → the real verb.
3. **Inline the one-use abstractions.** A helper used once? Inline it. A factory with one implementation? Delete the factory. An interface with one implementer? Delete the interface. A config object with one entry? Use the value directly.
4. **Remove the defensive bloat.** Delete null checks for things that can't be null (after boundary validation). Delete try/catch blocks that swallow errors. Delete "just in case" branches that can't run.
5. **Match the neighbours.** Read the files around the change. Match their naming, their comment density, their structure. If the file uses short names, use short names. If it has no comments, add none.
6. **Delete the emoji and hype.** No emoji anywhere. No "comprehensive", "robust", "seamless", "production-ready".
7. **Add the real decision.** If the code makes a trade-off, say so in one short comment. `// Simple version — fine for <1000 rows.` This is the single most human thing a codebase can contain.

## Before / after
```js
// BEFORE — AI code
/**
 * Validates the user's email address.
 * This function checks that the email contains an @ symbol
 * and a valid domain part. Returns true if valid, false otherwise.
 * @param {string} email - The email address to validate.
 * @returns {boolean} - True if the email is valid.
 */
function validateUserEmail(email) {
  if (!email || typeof email !== 'string') {
    return false;
  }
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  const result = emailRegex.test(email);
  return result;
}
```

```js
// AFTER — human code
function isValidEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}
```

## Rules
- **Don't change the behavior.** Humanizing is a style pass, not a refactor. Tests must pass before and after, unchanged.
- **Don't fake mistakes.** No deliberate typos, no fake bugs, no sloppy formatting. Human code is good code.
- **Small diff.** If the humanize pass touches more lines than the original change, it's too big. The goal is fewer lines, not a rewrite.
- **Keep the good parts.** If the AI code has a genuinely good name or a genuinely useful comment, keep it. Humanizing removes tells, it doesn't rewrite everything.
- **Verify.** Run the ai-tells checklist (`references/ai-tells.md`) after the pass. Every box should be checked.
