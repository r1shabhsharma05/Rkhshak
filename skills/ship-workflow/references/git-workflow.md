# Git Workflow — trunk-based, atomic, clean, finished

Distilled from three sources, in our own words: git-workflow-and-versioning (MIT), using-git-worktrees (MIT), finishing-a-development-branch (MIT). Full procedures live in those sources. Use when making any code change, committing, branching, resolving conflicts, or finishing a branch.

## Core principles
- **Trunk-based development (recommended).** Short-lived branches off the main line; merge back quickly. A branch that lives for weeks is a merge conflict in waiting.
- **Commit early, commit often.** A commit is a save point, not a ceremony.
- **Atomic commits.** One commit, one self-contained change. Everything mixed into one commit is a review that cannot be read.
- **Descriptive messages.** Explain intent (why), not what the diff already shows. Lowercase, human, short.
- **Keep concerns separate.** Separate concerns get separate commits.
- **Size your changes.** Small changes review, test, and revert better than large ones.

## Branching
Feature branches with clear names (`fix/<issue>-<slug>`, `feat/<name>`). One branch per concern. Delete the branch after it merges.

## Working with worktrees
When feature work needs isolation from the current workspace (parallel agents, a long-running branch, a plan execution), create an isolated workspace first:
- **Detect existing isolation.** Check whether you are already in a worktree or a submodule — treat each accordingly.
- **Create the workspace.** Prefer native worktree tooling; fall back to `git worktree` with a project-local directory (never outside the project root without approval).
- **Set the project up** in the new workspace (install dependencies for the stack in use), then **verify a clean baseline** (tests green) before starting. Report the workspace path and the baseline result.
- When done, merge and clean up: remove the worktree after the merge is verified.

## The save point pattern
Before a risky operation, commit or stash a save point. A save point is cheap; a lost afternoon is not.

## Pre-commit hygiene
Before every commit: check what is about to be committed (read the diff); ensure no secrets; run the tests for the touched area; run linting; run type checking. Generated files are committed only when the project does — otherwise they are ignored.

## Using git for debugging
Bisect to find the commit that introduced a bug (check out midpoints, run the test at each); view what changed recently; find who last changed a line; search commit messages for a keyword. See `codebase-intelligence` `references/commit-archaeology.md`.

## Release & versioning
Semantic versioning; tag the release and let the tag be the source of truth; keep a changelog written for humans (see `coding-craft` docs).

## Finishing a development branch
1. **Verify tests.** The branch's tests pass, and the full suite passes on the merged result — not just on the branch.
2. **Detect the environment.** Capture the workspace path and branch now — cleanup later changes directory.
3. **Determine the base branch.** The branch this work merges into (usually the main line).
4. **Present options.** Merge locally, push and create a PR, or keep as-is. The user picks; the agent does not assume.
5. **Execute the choice.** Merge first and verify success before removing anything; verify tests on the merged result. For a PR from a detached HEAD, name the new branch on the remote when pushing. If the user asks to discard the work, confirm explicitly first — discarding is irreversible.
6. **Cleanup the workspace.** Remove the worktree or branch only after the merge is verified.
