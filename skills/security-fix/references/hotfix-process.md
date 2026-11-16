# Hotfix Process — emergency fix for a live vulnerability

A vulnerability is live in production. This is the process: fast, narrow, and honest. Speed matters, but a rushed fix that breaks the app or hides the problem is worse than a slow one.

## The flow
### 1. Triage (minutes, not hours)
- Severity: is it being exploited right now? Can it be? What data is at risk?
- Critical (exploitable now, data at risk) → fix immediately, everything else waits.
- High (exploitable, but needs a condition) → fix today.
- Anything lower → normal fix flow (`security-fix` skill), not a hotfix.

### 2. Contain first, fix second
- If the vulnerability can be contained without a code change, do that first: block the endpoint (WAF / rate limit / feature flag off), rotate the exposed key, disable the feature.
- Containment buys time for a correct fix. A contained vulnerability is not a fixed one — the fix still ships, but the bleeding stops now.

### 3. Smallest complete fix
- One finding, one focused change. No refactoring, no features, no "while I'm here". The hotfix touches the minimum code that closes the hole.
- Use the known-good pattern (`references/fix-patterns.md`). Don't invent a fix under pressure.

### 4. Test fast, test the right thing
- Re-run the exact attack that proved the vulnerability. Watch it fail now.
- Run the test suite. If it's red, the hotfix broke something — fix that before shipping, or roll back and re-do it.
- If there's no time for a full test run, test the changed endpoint + login + the main feature. Say what wasn't tested.

### 5. Deploy + verify on live
- Deploy. Then verify on live — the same attack, against the live app, with fresh evidence. A hotfix verified only locally is not verified.
- Watch the error rate and the affected endpoint for an hour after deploy.

### 6. Disclose + record
- Tell the user what happened, what was at risk, what was fixed, and what remains (if anything). No downplaying.
- Record it: finding, severity, timeline (found → contained → fixed → verified), what was at risk, who was affected.
- If user data was exposed, the user decides on disclosure to affected users — the agent never hides a breach.

## What a hotfix is NOT
- Not a redesign. Not a refactor. Not a feature.
- Not a silent fix. A live vulnerability that gets fixed without a record is a vulnerability nobody learns from.
- Not a reason to skip verification. A hotfix that isn't verified on live is a guess.

## The checklist
- [ ] Severity decided (Critical / High / lower)
- [ ] Contained (endpoint blocked / key rotated / feature off) — if possible
- [ ] Smallest complete fix written (pattern from `fix-patterns.md`)
- [ ] Attack re-run — fails now
- [ ] Test suite green (or: what wasn't tested, named)
- [ ] Deployed + verified on live
- [ ] Error rate watched after deploy
- [ ] Recorded: finding, timeline, risk, who was affected
