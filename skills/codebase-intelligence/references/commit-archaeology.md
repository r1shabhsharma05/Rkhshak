# Commit Archaeology — reconstruct why code exists

Distilled from the commit-archaeologist skill (MIT) and its `reading-git-history.md` reference. Method in our own words; the full dig procedure lives in that source. Use when the question is why code exists, when it changed, or who to ask about it — never to assign blame.

## When to use
- "Why is this here?" — a strange line, a workaround, a magic constant.
- "When did this break?" — bisect a regression to its introducing commit.
- "Who owns this?" — current authors and recent changers of a file.
- "What else changed with it?" — companion files that always move together.

## When not to use
- The history is shallow, squashed, or rewritten: say so, and fall back to the docs and the code itself.
- To judge a person. History explains decisions; it does not grade people.

## Run the dig
1. **Gather the target.** The file, function, or line range in question, plus the repo root.
2. **Find the introducing commit.** Log the history of the target lines; the commit that first added them is the origin. Read its message in full.
3. **Follow later changes.** Log subsequent touches: what changed, when, and what each message says. A fix commit often explains the original better than the original does.
4. **Find companion files.** Files that change in the same commits, repeatedly, are part of the same intent — check them before concluding.
5. **Identify current authors.** Who touched it most recently and most often; they are the people to ask, not the original author alone.

## Write the report
- The likely intent, in one paragraph, with the commits that support it.
- The introducing commit (hash + message) and the key later commits.
- Companion files and current authors.
- What is still uncertain, stated plainly. "Unknown" is a valid finding.

## Evidence rules
- Every claim cites a commit hash. No hash, no claim.
- A commit message is evidence about what the author believed at the time, not proof the belief was right.
- If two commits contradict each other, report both — do not pick the convenient one.
