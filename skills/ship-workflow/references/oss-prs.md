# Open-Source PRs — the four-phase pipeline and the fork handoff

Distilled from two sources, in our own words: github-oss-prs (MIT) and github_fork_pr_handoff. Full procedures live in those sources. Use when finding, solving, and submitting an open-source issue, or when handing a fork branch to a maintainer.

## The four phases
1. **Finding and selecting the right issue.** Filter by beginner labels (`good first issue`, `beginner-friendly`, `help wanted`). Verify availability: read recent comments — the issue must be active, unassigned, with no linked PR and a clear objective. Claim respectfully where the repo's culture requires it (a brief comment with a proposed solution, only when the contribution guide asks for assignment). Issue sources: curated `good first issue` feeds, issue-triage sites, up-for-grabs lists, and GitHub search itself (`is:issue is:open label:"good first issue" no:assignee`, sorted by recent activity).
2. **Project setup and exploration.** Read the README and the CONTRIBUTING file in full: setup, code style, test commands, PR template, label rules, auto-close bots. Check the LLM and AI-usage policy first — a repo that bans or auto-closes AI-assisted PRs is rejected; never misrepresent LLM use, and never "humanize" code to evade detection. Fork and clone; one dedicated branch per issue. Never commit secrets, API keys, or `.env` files.
3. **Solving and testing.** Reproduce first: confirm the bug or the missing feature locally before writing code. Focused changes only — concise, targeted at the issue, no unrelated refactoring. Verify and lint: run the repo's tests, linters, and type checks for the touched area.
4. **Submitting and iterating.** Clear commit messages; push the branch to the fork. The PR describes the fix, references the issue (`Fixes #NN`), and details the testing performed. Address maintainer feedback promptly, on the same branch.

## Pre-submission checklist (every PR, no exceptions)
- Issue understood; the repo's contribution rules respected.
- Tests, lint, and checks pass locally for the touched area.
- The diff reviewed — no secrets, no API keys, no stray files.
- The PR description links the issue and outlines the test results.
- The quality bar per PR: a real unsolved issue, the smallest correct fix, verified by the repo's own tests. Counts are targets, never quotas — fewer qualifying issues means fewer PRs and an honest report, never padded work.

## The fork PR handoff (when the push route cannot create the PR)
1. **Confirm the fork branch first.** Identify the upstream owner, repo, and base branch, and the fork owner and branch, from the push result. Confirm the fork branch exists on the remote with the exact name that was pushed.
2. **Build the fork-qualified compare link.** On the upstream repo: `https://github.com/<upstream-owner>/<repo>/compare/<base>...<fork-owner>:<branch>`. Do not shorten it or drop the fork owner — an upstream-only link points at upstream branches and shows no fork changes.
3. **Hand the link and verify the diff.** Present exactly one compare link, with the upstream repo, base branch, fork owner, and fork branch named alongside it in plain text, so a wrong owner is visible before clicking. Ask the user to confirm the compare page shows the fork branch diff and file list before creating the PR. If the page says there is nothing to compare, rebuild the link from the push result instead of resending the same link; check the fork owner spelling, the branch spelling, and whether the push actually landed.
