# Secret Rotation Playbook — step by step, in order

A secret leaked. The order is everything: rotate first, remove second, purge last. A purge without rotation leaves a live key in an attacker's hands.

## The steps (never skip, never reorder)
### 1. Identify the blast radius
- What secret is it (which service, which key), where does it appear (file:line, commit, log, chat), and who could have seen it (public repo = everyone).
- Is it live? Try it (or check the provider's dashboard). Assume live until proven dead.

### 2. Rotate / revoke FIRST
- Create the new secret. Deploy it everywhere the old one was used (backend, app, CI, dashboards). Verify the new one works.
- THEN revoke the old one. The old secret must stop working — test it and watch it fail.
- Never revoke before the replacement is live, or the app breaks. Never leave the old secret live "until we get around to it".

### 3. Remove it from the code
- Replace every occurrence with an env var / secrets manager reference. No secret in code, config, or a committed file.
- Check every branch, every fork, every copy of the repo the team controls.

### 4. Purge it from history (only after rotation, only with approval)
- Rewriting history is destructive: it needs a force-push, and every collaborator must re-clone. Get the user's explicit approval first.
- Use `git filter-repo` (or BFG) with the exact secret value. Verify the purge: the secret no longer appears in any commit.
- Tell every collaborator to re-clone. A stale clone re-pushes the secret back.

### 5. Verify
- The old secret fails everywhere (try it).
- The new secret works everywhere (the app runs, the tests pass).
- A fresh secrets scan (gitleaks / trufflehog) is clean.
- The provider's dashboard shows the old key revoked.

### 6. Record it
- What leaked, when, where, what was rotated, when the old key died, when the purge happened. This is the incident record — it goes in the audit report, not in chat.

## Common mistakes
- **Purge before rotation.** The history is clean but the key still works. The attacker doesn't care about your git history.
- **Rotating in one place only.** The key lives in Vercel AND in the app AND in CI. Rotate everywhere or the old key still has a home.
- **Forgetting the copies.** A fork, a backup, a screenshot in a doc, a key pasted in chat. The secret is wherever it was written, not just where you remember writing it.
- **Not testing the old key.** "We revoked it" is a claim. Trying it and watching it fail is evidence.

## The checklist (one per leaked secret)
- [ ] Secret identified (service, value scope, locations)
- [ ] New secret created + deployed everywhere
- [ ] New secret verified working
- [ ] Old secret revoked
- [ ] Old secret tested — fails
- [ ] Removed from code (all branches, all copies)
- [ ] Purged from history (approved, verified, collaborators re-cloned)
- [ ] Fresh scan clean
- [ ] Incident recorded
