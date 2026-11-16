# Vibe-Code Fixes — 20 things to fix on a vibe-coded website

The quick-fix list for a website that was vibe-coded and shipped without a review. Run it on any website before launch, and on any existing site that feels broken. Each item is a concrete check — pass or fail, no judgment calls.

## The 20 fixes
| # | Fix | What "fixed" looks like |
|---|---|---|
| 1 | **No horizontal scroll** | The page never scrolls sideways at any width (360px–1920px). If it does, something overflows — find the element, fix the width. |
| 2 | **No broken links** | Every link on the page leads somewhere real. Click every link (including footer, nav, and social icons). A link to `#` or nowhere is a broken link. |
| 3 | **Mobile menu** | On mobile, navigation is a working menu (hamburger or bottom bar). Every nav item is reachable. The menu closes after a tap. |
| 4 | **Favicon** | The tab shows the product's favicon, not the framework default. It works in light and dark browser chrome. |
| 5 | **Page titles** | Every page has a real `<title>` (product name + page name). No "Untitled", no "Vite + React", no duplicated titles. |
| 6 | **Meta description** | Every page has a real meta description (one plain sentence about the page). It shows correctly when the link is shared. |
| 7 | **Footer links** | Every footer link works and goes to a real page. No dead links, no `#`, no "coming soon" pages that don't exist. |
| 8 | **Custom 404 page** | A missing URL shows a 404 that looks like the product, says the page doesn't exist, and offers the way back. Never the framework default. |
| 9 | **Copyright year** | The footer shows the current year (or a correct range). Not last year, not a hardcoded 2023. |
| 10 | **Compressed images** | Images are compressed and sized for their display size (no 4MB hero, no 2000px image in a 400px slot). WebP/AVIF where supported, `loading="lazy"` below the fold. |
| 11 | **No broken buttons** | Every button does something. Click every button — a button that does nothing (no handler, no link, no feedback) is broken. |
| 12 | **Success messages** | After a successful action (form submit, save, purchase), the user sees a specific confirmation: what happened, to whom/what. Not "Success!" alone. |
| 13 | **Error messages** | When something fails, the user sees what happened + what to do next, in plain words. Never a blank screen, never a raw error, never "something went wrong" with no next step. |
| 14 | **No placeholder text** | No lorem ipsum, no "Your text here", no "Coming soon" blocks, no fake names (John Doe, Acme). Every word on the page is real or clearly marked to replace. |
| 15 | **No unused nav** | Every nav item leads to a real page with real content. A nav item that goes nowhere (or to an empty page) is deleted, not hidden. |
| 16 | **No mobile overflow** | On a 360px screen, nothing overflows, nothing is cut off, no text runs off the edge, no button is unreachable. |
| 17 | **Clickable logo** | The logo links to the home page. Always. On every page. |
| 18 | **Clickable phone number** | Phone numbers are `tel:` links. Tapping one on a phone starts a call. |
| 19 | **Clickable email** | Email addresses are `mailto:` links. Tapping one opens the mail app. |
| 20 | **Mobile optimized** | The whole site works on a phone: readable text (16px+), tappable targets (44×44px), no pinch-to-zoom needed, forms usable with a thumb. |

## How to run it
1. Open the site on desktop and on a 360px mobile viewport.
2. Click every link and every button. Scroll every page. Submit every form (with good and bad input).
3. Mark each of the 20 items PASS or FAIL with the evidence (which link, which button, which page).
4. Fix every FAIL before launch. This list is a launch gate for vibe-coded sites — a FAIL is not "polish", it's broken.
