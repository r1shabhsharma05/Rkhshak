# UX Patterns — 20 patterns every SaaS needs (design version)

The design implementation of the 20 SaaS UX patterns. Each pattern has the design rule — what to build and how it should feel. A checklist version (with security overlap mapping) also lives in the security-audit skill as `ux-patterns-checklist.md`; this file is the design guide, not a duplicate.

## The 20 patterns
| # | Pattern | Design rule |
|---|---|---|
| 1 | **Optimistic UI Updates** | The UI updates immediately on the user's action, then confirms with the server. If the server fails, roll back visibly and say what happened. Never make the user wait for a spinner on a routine action. |
| 2 | **Skeleton Loaders** | Loading shows a skeleton that matches the final layout (same shapes, same positions) — never a generic spinner, never a blank screen, never a skeleton that doesn't match what loads. |
| 3 | **Command Palette** | `Cmd/Ctrl + K` opens a palette: search actions, navigate, run commands. Fuzzy search, keyboard-first, results ranked by relevance. Every major action is reachable from it. |
| 4 | **Persistent Sidebar Navigation** | The sidebar stays visible across the app (not hidden behind a hamburger on desktop). Active item is clearly marked. Sections are grouped by job, not by team. |
| 5 | **Loading and Empty States** | Every list, card, and screen has a designed loading state AND a designed empty state (see `content-states.md`). Empty is not blank — it says what goes here and the one action to fill it. |
| 6 | **Autosave Functions** | Changes save automatically. The user sees the save state ("Saving…", "Saved", "Saved 2 min ago") near where they edited. Never lose work to a refresh. |
| 7 | **Debouncing** | Search, filters, and live inputs wait for the user to pause (200–300ms) before firing. No request per keystroke, no flicker. |
| 8 | **Throttling** | Rapid actions (scroll, resize, drag) fire at most once per interval. The UI stays smooth under fast input. |
| 9 | **Smart Form Validation** | Validate as the user types (not only on submit), show the error next to the field, in plain words, with the fix. Don't clear the form on error. Don't validate a field the user hasn't touched yet. |
| 10 | **Bulk Actions On List** | Select multiple rows, act on all of them at once (delete, archive, export, assign). The selection is visible, the actions are clear, destructive bulk actions confirm first. |
| 11 | **Reusable Data Table** | One table component used everywhere: sortable columns, resizable where it matters, row actions, pagination or infinite scroll — consistent across the whole app. |
| 12 | **Advanced Data Filtering** | Filters combine (search + status + date + owner), are visible, removable one by one, and shareable (the filtered view has a URL). Never hide the active filters. |
| 13 | **Keyboard Shortcuts** | The common actions have shortcuts (new, save, search, navigate). Shortcuts are discoverable (a `?` menu or a shortcuts page) and don't conflict with the browser. |
| 14 | **Tier-Based UI Indicators** | The user's plan is visible where it matters (usage bar, feature locks, upgrade prompts). Locked features show what the plan includes, not a dead end. Upgrade is one clear action, not a maze. |
| 15 | **Onboarding Data Capture** | Onboarding asks for the minimum needed to make the product useful — one thing per step, skippable where possible, and the product is usable after step one, not after step ten. |
| 16 | **Referral and Affiliate Pages** | A page where the user finds their link, their rewards, and their referrals — with real numbers, not a generic "invite friends" banner. |
| 17 | **Custom 404 Page** | A 404 that looks like the product, says plainly the page doesn't exist, and offers the way back (home, search, the main sections). Never the framework default. |
| 18 | **Mobile-Optimized SaaS Layouts** | The app works on a phone: sidebar becomes a bottom bar or a drawer, tables become cards or horizontal scroll, touch targets are 44×44px, nothing overflows. |
| 19 | **Destructive Action Protection** | Delete/destroy asks first — a confirmation that names what will be deleted and the consequence, with the dangerous action visually distinct. Undo where possible. |
| 20 | **Graceful Error Recovery** | When something fails, the user gets: what happened (plain words), what to do next, and a way to retry. Never a blank screen, never a stack trace, never "something went wrong" with no next step. |

## Rules
- **A pattern is present only when it works.** A command palette that doesn't search, a skeleton that doesn't match the layout, a 404 that is the framework default — these are not the pattern, they're a placeholder.
- **Patterns serve the job.** Don't add a pattern because the list says so. If the product has no list, it needs no bulk actions. If it has no search, it needs no command palette.
- **Consistency.** The same pattern behaves the same way everywhere in the app. One table, one palette, one empty-state style.
- **These are product expectations, not a security gate.** A missing pattern is a UX gap, never a security vulnerability — and UX completeness never excuses a security failure.
