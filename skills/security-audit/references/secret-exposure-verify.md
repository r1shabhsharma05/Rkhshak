# Secret Exposure Verification — prove "no leak" before claiming it

A clean root directory is no evidence about the rest of the repo. "No leak" is a claim that must be earned by checking every path, the full history, and the remote — and naming what was checked. Use this alongside `references/secrets-scanning.md` whenever the question is whether a secret is exposed.

## Check every path, not just the root

- List every environment-file path in the repository, including nested directories (for example `server/`, `backend/`, service subfolders), before making any claim about a leak.
- Search the tracked file list for all names matching `.env`, `.env.local`, `.env.production`, and similar patterns, and record each path found.
- Treat a clean root directory as no evidence about nested directories, and never report a repository-wide result from a root-only check.
- Check the ignore file only to explain how a file got in — never use an ignore entry as proof that a file is absent from the remote.

## Check history and the remote

- Search the full git history for every environment-file path listed, including deleted files and files added in any branch.
- Fetch each candidate path from the remote default branch through its raw file URL, and treat an HTTP 200 response that returns file content as public exposure.
- Treat an HTTP 404 response as evidence only for that exact path and branch, and repeat the fetch for every other candidate path.
- Record the exact path, branch, and response for each check, so a later reader can repeat it without guessing what was checked.

## Report only what the checks prove

- Report "no leak" only after every path, history, and remote check above is complete, and name the paths and branches checked.
- Report an exposure at once when any check returns file content, name the exposed paths, and say the keys in those files must be **rotated before any history cleanup** (see `references/secrets-scanning.md` and `security-fix` (`security-fix/references/secret-rotation.md`)).
- Never quote a secret value, key, or token from an exposed file in the report — name only the file path and the kind of secret it held. Show at most its first 4 characters + file:line, and only when needed as an example.
- Correct the earlier report in the same conversation when a later check finds an exposure the first check missed, and name the path the first check missed.

## What counts as a finding

- An environment file present in the tracked files or in history on any branch: **finding**, even if the current branch looks clean.
- A raw-URL fetch returning file content: **confirmed public exposure**.
- A check that could not be run (no remote access, history unavailable): **CAN'T VERIFY**, with the exact missing check named — never "no leak".

## Provenance

Summarised in our own words from the verify-secret-exposure workflow (check every path, history, and remote before claiming no leak).
