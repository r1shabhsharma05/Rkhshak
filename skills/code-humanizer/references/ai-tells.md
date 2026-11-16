# AI Tells — the giveaways that code was AI-written

A reviewer spots AI code by its tells. Learn them, then remove them. Each tell has a fix.

## 1. Verbose comments explaining obvious things
```js
// BAD — the code already says this
// Increment the counter by 1
count += 1;

// BAD — a tutorial in a comment
// This function validates the user's email address by checking
// that it contains an @ symbol and a domain part. It returns
// true if valid and false otherwise.
function isValidEmail(email) { ... }
```
**Fix:** delete the comment. If the code needs a comment to be understood, rename things until it doesn't. Comments explain WHY, never WHAT.

## 2. A docstring on every function
```python
# BAD
def calculate_total(items):
    """
    Calculate the total price of all items.

    Args:
        items (list): A list of item dictionaries, each with a 'price' key.

    Returns:
        float: The total price of all items.
    """
```
**Fix:** a one-line comment only where the function does something surprising. Most functions need no comment at all.

## 3. Generic names
`data`, `result`, `handler`, `utils`, `manager`, `processData`, `getInfo`, `doSomething`, `item1`, `temp`.
**Fix:** name things by the domain: `invoice`, `unpaidInvoices`, `sendInvoice`, `overdueCount`. If a name could fit any project, it's too generic.

## 4. Over-abstraction
A factory for one implementation. An interface with one implementer. A config object with one entry. A helper function used once for a one-liner. A `BaseService` with one subclass.
**Fix:** inline it. Abstraction earns its place only when there are two real uses. One use = inline. Renaming the helper is not a fix — the layer must disappear, not get a better name. If the one-use layer is exported, keep the export name but point it at the inlined implementation (re-export the surviving function); never rename or delete the export, and never break callers.

## 5. Defensive code everywhere
```js
// BAD — checking for things that can't happen
if (user && user.name && user.name.first && typeof user.name.first === 'string') { ... }
try { ... } catch (e) { /* swallow */ }
```
**Fix:** validate at the boundary (input, API response), trust the data after that. Never swallow an error silently.

## 6. Perfect, uniform structure
Every function the same length. Every file the same layout. Everything alphabetically ordered. Every error handled the same way. Real codebases are uneven — some files are tidy, some are messy, because they were written at different times by different people.
**Fix:** match the local file's style. Don't reformat a whole file to match your new code.

## 7. Emoji in comments or logs
`// ✅ Done!`, `// 🚀 Launch!`, `console.log('🎉 Success!')`.
**Fix:** delete the emoji. Logs and comments are plain text.

## 8. Hype and filler words in comments
`// This is a robust, scalable, production-ready solution that seamlessly handles...`
**Fix:** delete the adjectives. Say what it does, in plain words, or say nothing.

## 9. "Comprehensive" everything
`comprehensive validation`, `complete solution`, `fully handles all edge cases` — in comments, function names, or commit messages.
**Fix:** describe the specific thing it does, not how complete it claims to be.

## 10. No TODOs, no trade-offs, no opinions
AI code is always "complete" and never admits a limitation. Human code has a `// TODO: handle rate limit retries` or a comment saying "this is slow for large lists, fine for now — we have <1000 rows".
**Fix:** if there's a real limitation or a real decision, say so in a short comment. A code with no trade-offs is a code that hides them.

## 11. Over-typed, over-annotated
Type annotations on every variable, even when the type is obvious from the value. Interfaces for simple objects.
**Fix:** annotate where the type isn't obvious. Let inference do its job.

## 12. Alphabetical imports / perfect grouping
Imports sorted perfectly, every import grouped by category, no unused import left behind — in a file the human has been editing for months.
**Fix:** match the file. If the file's imports are messy, leave them messy (or sort only your own additions).

## Quick check (run before shipping)
- [ ] No comment explains what the code already says.
- [ ] No docstring on a function whose name already explains it.
- [ ] No generic names (`data`, `result`, `handler`, `utils`).
- [ ] No abstraction with one use.
- [ ] No defensive check for something that can't happen.
- [ ] No emoji, no hype words, no "comprehensive".
- [ ] At least one real decision is visible (a comment, a name, a trade-off).
- [ ] It matches the files around it.
