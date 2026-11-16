# Vibe-Code Security Checklist — merged, mapped to the 85 checks

Two viral "vibe-coded app" security checklists (udayan.builds + the 19-item list), merged and mapped to the 85-check audit. Every item here is already covered by an 85-check area — this file exists so the auditor can verify none of these popular checks is missed. If an item's 85-check area passes, this item passes. If it fails, the 85-check finding is the one to report.

## List A — udayan.builds (18 items)
| # | Check | 85-check |
|---|---|---|
| 1 | Hide API keys | 1.1 |
| 2 | Protect admin routes | 3.3 |
| 3 | Users access own data | 3.1 |
| 4 | Block XSS | 5.2 |
| 5 | Check CORS settings | 6.2 |
| 6 | Debug mode OFF in prod | 10.2 |
| 7 | Remove unused packages | 9.1, 11.3 |
| 8 | Secure database | 4.1, 4.4, 4.5 |
| 9 | Secrets in git history (rotate + replace) | 1.2 |
| 10 | Check env variables | 1.3 |
| 11 | Proper authentication | 2.1–2.7 |
| 12 | Sanitize forms | 5.1 |
| 13 | Rate limiting | 6.1 |
| 14 | Security headers | 10.1 |
| 15 | Update dependencies | 9.1 |
| 16 | Check exposed files | 10.4 |
| 17 | Hash passwords | 2.2 |
| 18 | Full security audit | (this skill — the 85-check audit) |

## List B — 19-item security checklist (01/19 FIXED)
| # | Check | 85-check |
|---|---|---|
| 1 | Row level security | 4.5 |
| 2 | Auth on every API route | 2.1 |
| 3 | Never trust the frontend | 3.1, 5.1 |
| 4 | Rate limiting | 6.1 |
| 5 | Sanitize user input | 5.1 |
| 6 | Parameterized queries | 4.1 |
| 7 | Lock down CORS | 6.2 |
| 8 | HTTPS everywhere | 13.2 |
| 9 | Stop IDOR bugs | 3.1 |
| 10 | Debug mode off in prod | 10.2 |
| 11 | CAPTCHA on public forms | 6.3 |
| 12 | Log admin actions | 10.5 |
| 13 | Private storage buckets | 4.3 |
| 14 | Hide admin pages properly | 3.3 |
| 15 | Update vulnerable packages | 9.1 |
| 16 | Check file upload types | 5.3 |
| 17 | Security review (this audit) | (this skill) |
| 18 | Security headers | 10.1 |
| 19 | Verify webhook signatures | 6.6 |

## How to use
- Run the 85-check audit. For each item above, confirm its mapped 85-check area was run and list the evidence. Do not re-run these as a separate pass — they are the same checks, grouped the way viral checklists present them.
- "Debug mode" and "unused packages" are FAILs when present, not passes — the reel's ✗ means the app still has them.
