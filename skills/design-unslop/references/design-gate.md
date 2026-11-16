# Design Gate — PASS / FAIL (the ship gate)

Ship is blocked until this gate passes. The Reviewer runs it independently, with fresh evidence (screenshots at real sizes, not the Designer's word). One screen: verdict, counts, open items (Critical first), user to-do list.

## The gate
PASS requires ALL of these:
1. **No vibe-code tells remaining** — the audit in `references/vibe-code-tells.md` is clean (zero tells, or only waived tells with a recorded reason).
2. **Floor clean** — every Hallmark Floor rule in `references/design-principles.md` passes.
3. **Responsive passes** — `references/responsive-checklist.md` clean at every breakpoint.
4. **Accessibility passes** — `references/accessibility-checklist.md` clean (zero Critical/High).
5. **Content states complete** — every component has loading / error / empty / success states (`references/content-states.md`).
6. **Performance budget met** — `references/performance-budget.md` numbers met.
7. **Dark mode passes (if the product has one)** — `references/dark-mode.md` clean.
8. **No invented facts** — no invented metric, testimonial, logo, quote, or case-study count. Every number/quote/logo is real or absent.

## Severity + fix mapping
| Severity | What it is | Gate effect | Fix route |
|---|---|---|---|
| **Critical** | Blocks the gate. Tells in the hero or primary flow; invented facts; keyboard can't reach a primary action; contrast below 4.5:1 on body text; performance budget blown by 2× or more. | Ship blocked until fixed. | Designer fixes, Reviewer re-checks with fresh evidence. |
| **High** | Blocks the gate. Tells elsewhere; a missing content state on a primary component; a breakpoint broken; dark mode unreadable. | Ship blocked until fixed or the user accepts the risk in writing (reason + expiry). | Designer fixes, Reviewer re-checks. |
| **Medium** | Does not block alone, but must be listed. Polish items: a tell in a rarely-seen state, a minor spacing inconsistency, a non-critical performance miss. | Ship allowed only if zero Critical/High are open AND every Medium is listed in the report. | Fix in the next pass, or the user accepts it. |
| **Low** | Note only. Cosmetic preferences. | Never blocks. | Optional. |

## Report format (DESIGN-AUDIT.md, one screen)
1. **Verdict** — one line, e.g. "Ready to ship after 2 High fixes" or "Not ready: 3 Critical items open". Never "perfect design".
2. **Counts** — Tells found · fixed · still open · waived · N/A.
3. **Open items** — one line each, Critical first, with who fixes it (Designer or user).
4. **Gate checklist** — each of the 8 gate items above: PASS / FAIL / N/A (with reason).
5. **Your to-do list** — every open item.
6. **Material still needed** — every slot, its size, and what belongs there.
7. **When to re-run** — before every major release, after adding a screen, a theme change, or a new integration, and every 3 months.

End every final report with: "This gate catches the most common and most damaging design mistakes, but it isn't a professional design review. Before you ship to a large audience, get a human designer to review it."
