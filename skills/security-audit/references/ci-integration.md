# CI Integration — run the audit on every PR

The skill tells you what to check. This file tells you how to automate it, so the audit runs on every pull request and blocks a merge when the gate fails.

## What to automate (and what stays manual)
| Check | Automate in CI? | How |
|---|---|---|
| Dependency audit (`npm audit` / `pip-audit`) | Yes | Run on every PR; fail on Critical/High. |
| Secret scan (committed secrets) | Yes | Scan every commit (e.g. gitleaks, trufflehog, or GitHub secret scanning). Fail on any finding. |
| Security headers (live probe) | Yes | Probe the preview deployment's headers; fail if required headers are missing. |
| Lint / typecheck / tests | Yes | Existing suite; fail on any failure. |
| Full 85-check audit | No | Needs judgment, live probing, and human checks (H1–H18). Run it by hand before a release. CI runs the automatable subset. |
| Human checks (H1–H18) | No | Only a human can answer. CI can't rotate a secret or test two accounts. |

## GitHub Actions workflow template (copy, adapt to the project)
```yaml
name: security-checks
on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Dependency audit
        run: |
          npm audit --audit-level=high
          # or: pip-audit --desc
      - name: Secret scan
        uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - name: Security headers (preview)
        run: |
          # Replace with the preview URL for this PR
          curl -sI ${{ env.PREVIEW_URL }} | grep -i "strict-transport-security\|content-security-policy\|x-content-type-options"
```

## Rules
- **CI is a net, not a proof.** A green CI run means the automatable checks passed. It does NOT mean the app is secure. The full 85-check audit still runs by hand before a release.
- **Fail the build on Critical/High.** A dependency with a Critical vulnerability blocks the merge. No "we'll fix it later" — fix it, or record a written risk-acceptance (reason + expiry) in the PR.
- **Secrets in CI are masked.** Never print a secret in CI logs. Use the platform's secrets store, never a hardcoded value in the workflow file.
- **Pin action versions.** Use exact versions (`actions/checkout@v4`, not `@main`). Unpinned actions can change under you.
- **The workflow file itself is audited.** The workflow runs with the repo's permissions — least privilege (read-only where possible), no `pull_request_target` with checkout unless the risk is understood.
