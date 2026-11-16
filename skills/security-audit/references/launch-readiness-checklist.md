# Launch Readiness Checklist — merged, mapped to the 85 checks

Four viral pre-launch checklists merged and deduped: "20 things before launching your website", "11 things to check in your vibe-coded website", the 21-item launch list, and the 20-item launch list. Each item maps to an 85-check area where it overlaps; the rest are Launch (SEO / performance / accessibility / UX / legal) items, not security — they are included because the user wants one complete pre-launch gate, but they do not count toward the security gate. A Launch item failing never blocks the security gate, and a security item failing is never excused by Launch items passing.

## Security items (map to the 85 checks)
| Check | 85-check | Sources |
|---|---|---|
| Privacy policy page | 12.1 | 20-things, 11-checks, 20-launch |
| Terms and conditions page | 12.1 | 20-things, 11-checks, 20-launch |
| Cookie policy | 12.2 | 11-checks |
| Refund policy | H9 | 11-checks |
| Cookie consent banner | 12.2 | 20-things, 21-launch |
| Cookie + form consent | 12.2, 5.1 | 11-checks |
| What user data you collect (stated) | 12.1 | 11-checks |
| Secrets / API keys off the frontend | 1.1 | 20-things, 20-launch |
| Force HTTPS | 13.2 | 20-things |
| Form validation (server-side) | 5.1 | 20-things, 20-launch |
| Spam / bot protection | 6.3 | 20-things |
| Security headers | 10.1 | 21-launch |
| Rate limiting | 6.1 | 20-launch |
| Database backups | H7 | 20-launch |
| Row level security | 4.5 | 20-launch |
| Real login and logout | 2.1, 2.5 | 20-launch |
| Password reset | 2.3 | 20-launch |
| Email verification | 2.3 | 20-launch |
| Clear error messages (no stack traces) | 5.6 | 20-launch |
| Error tracking | 10.5 | 20-launch |
| Delete account button | 12.3 | 20-launch |
| Third-party embeds (minimal, official source) | 9.4 | 11-checks |

## Launch items (not security — separate gate)
| Check | Category | Sources |
|---|---|---|
| Meta titles and descriptions | SEO | 20-things, 21-launch |
| Social preview image / Open Graph metadata | SEO | 20-things, 21-launch |
| Favicon | Launch | 20-things, 21-launch |
| Sitemap (XML) + robots.txt | SEO | 20-things, 21-launch |
| Canonical tags | SEO | 21-launch |
| Schema.org structured data | SEO | 21-launch |
| Breadcrumb navigation | UX | 21-launch |
| Internal linking between related pages | SEO | 21-launch |
| Alt text to images | Accessibility | 20-things, 11-checks |
| Colour contrast | Accessibility | 20-things, 11-checks |
| Keyboard-accessible controls / clear buttons | Accessibility | 11-checks |
| Reduced motion support | Accessibility | 21-launch |
| Compress images / WebP support | Performance | 20-things, 21-launch |
| Page load speed | Performance | 20-things |
| Lazy loading for off-screen images | Performance | 21-launch |
| Faster font loading | Performance | 21-launch |
| Make it mobile friendly / mobile layout | Launch | 20-things, 20-launch |
| Custom 404 page | UX | 20-things, 21-launch, 20-launch |
| Fix broken links | Launch | 20-things |
| Set up analytics | Launch | 20-things, 20-launch |
| Event tracking | Launch | 21-launch |
| Contact form with email notification | Launch | 21-launch |
| Toast notifications | UX | 21-launch |
| Loading states / skeleton loaders / empty states | UX | 20-launch, 21-launch |
| Onboarding flow | UX | 20-launch |
| One clear call to action | Launch | 20-things |
| Fake reviews / claims + legal compliance | Legal | 11-checks |
| Copyrighted images + applicable local laws | Legal | 11-checks |

## How to use
- Run the 85-check audit for the security items. Run the Launch items as a second, separate pass and report them under "Launch readiness", never mixed into the security counts.
- The security gate and the launch gate are independent. A site can pass security and fail launch (or vice versa) — report both verdicts separately.
