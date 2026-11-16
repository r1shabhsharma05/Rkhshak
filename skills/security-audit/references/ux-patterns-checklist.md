# 20 UX Patterns Every SaaS Needs

A UX / product-readiness reference, NOT a security checklist. Included because the user wants one complete pre-launch skill, but these patterns do not count toward the security gate. Where a pattern overlaps a security check, the mapping is noted — the security check is what gets verified, the UX pattern is the product expectation.

| # | Pattern | Security overlap |
|---|---|---|
| 1 | Optimistic UI Updates | — |
| 2 | Skeleton Loaders | — |
| 3 | Command Palette | — |
| 4 | Persistent Sidebar Navigation | — |
| 5 | Loading and Empty States | — |
| 6 | Autosave Functions | — |
| 7 | Debouncing | — |
| 8 | Throttling | 6.1 (rate limiting) |
| 9 | Smart Form Validation | 5.1 (server-side validation) |
| 10 | Bulk Actions On List | — |
| 11 | Reusable Data Table | — |
| 12 | Advanced Data Filtering | — |
| 13 | Keyboard Shortcuts | — |
| 14 | Tier-Based UI Indicator | 3.4 (plan limits enforced server-side) |
| 15 | Onboarding Data Capture | — |
| 16 | Referral and Affiliate Pages | — |
| 17 | Custom 404 Page | — |
| 18 | Mobile-Optimized SaaS Layouts | — |
| 19 | Destructive Action Protection | Confirm before delete/destroy; server must enforce it, not just the UI |
| 20 | Graceful Error Recovery | 5.6 (errors fail safely) |

## How to use
- Check each pattern is present and working in the app. Report missing patterns under "UX / product readiness", separate from security findings.
- Never present a UX gap as a security vulnerability, and never let UX completeness excuse a security failure.
