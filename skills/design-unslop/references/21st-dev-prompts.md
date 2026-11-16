# 21st.dev Prompts — find proven components instead of hand-building generic ones

21st.dev is a catalog of 10,000+ React + Tailwind components, themes, and templates. Use it BEFORE hand-building a component. A proven component, adapted to the direction and tokens, beats a hand-built generic one — and it never looks vibe-coded, because real people built and refined it.

## How to use it (the tools)
| Tool | What it does | Cost |
|---|---|---|
| `search` | Search the catalog by plain language. Returns id, name, description, and a preview screenshot. | Free (metadata only, unlimited for ordinary use). |
| `get_inspiration` | Give a natural-language brief, get component ideas back. | Free. |
| `get_component` | Fetch the full source of one component by its search-result `id`. | Paid step — draws from the daily retrieval quota on the free tier. Check quota first with `get_usage`. |
| `get_theme` | Fetch a theme by id. | Free metadata. |
| `search_logo` | Find brand logos by name (for real company marks only). | Free. |

**Workflow:** search (free) → look at the preview screenshots → pick the best 2–3 → fetch the code for the winner only (`get_component`) → adapt it to the direction + tokens → use it. Never fetch the code for 10 components and pick later — the quota is daily.

## Rules
- **Search before hand-building.** If 21st.dev has the component, use it. Hand-build only what the catalog doesn't have.
- **Adapt, don't paste.** The component takes the project's tokens (palette, type, radius, spacing) — it does not bring its own look. Every colour and font goes through a token. Restyle it to the direction before shipping.
- **Preview first.** Judge the preview screenshot, not the name. A component named "Modern Hero" can still be slop — run the vibe-code tells against the preview.
- **Never run an install URL that embeds a key.** The search result includes an install command with `?api_key=<key>`. Never run it. Fetch the code with `get_component` and add the files to the project by hand instead.
- **Respect the quota.** Code retrieval is the paid step. Search + preview as much as you want (free), fetch code only for the component you will actually use.
- **Credit the author.** The component's author is in the search result. Keep the attribution when the license requires it.
- **Third-party logos keep their real colors** (use `search_logo` for real marks only — never a fake logo wall).

## Prompt library — ready-made searches (copy the query, adapt the words in brackets)
Search with plain language: what the component IS + what it DOES + the feel. Be specific — "hero" returns everything, "animated hero with staggered text and product screenshot" returns the right thing.

| Need | Search query (prompt) |
|---|---|
| Hero (landing) | `animated hero section with staggered text and button reveal` |
| Hero (product) | `hero section with product screenshot and social proof stats` |
| Hero (minimal) | `minimal hero section small animations ux friendly` |
| Navbar | `responsive navbar with mobile menu and dropdown` |
| Dashboard sidebar | `dashboard sidebar navigation collapsible sections` |
| Dashboard cards | `dashboard stat cards with charts and trend indicators` |
| Pricing | `pricing table three tiers with highlighted plan and toggle monthly yearly` |
| Login / auth | `login form with social buttons and password visibility toggle` |
| Signup / onboarding | `onboarding multi-step form with progress indicator` |
| Cards (content) | `content card with image overlay and hover reveal` |
| Cards (product) | `product card with price rating and add to cart` |
| Testimonials | `testimonial carousel with avatars and company logos` |
| FAQ | `faq accordion with smooth expand collapse` |
| Footer | `footer with newsletter signup and link columns` |
| Modal / dialog | `modal dialog with backdrop blur and focus trap` |
| Table (data) | `data table with sorting filtering and pagination` |
| Form (contact) | `contact form with validation states and success message` |
| Empty state | `empty state illustration with call to action button` |
| Loading | `skeleton loader matching card layout` |
| Command palette | `command palette search with keyboard shortcuts` |
| Theme | `dark minimal theme for saas dashboard` (type: `theme`) |
| Template (landing) | `saas landing page template hero pricing testimonials` (type: `template`) |

## Inspiration briefs (for `get_inspiration`)
When you don't know what component you need, give `get_inspiration` a brief — one sentence with the product, the screen, and the job:
- "A calm invoicing app needs a dashboard that shows this month's revenue, unpaid invoices, and a quick action to send an invoice."
- "A fitness app needs an onboarding flow that asks for a goal, a level, and a schedule in 3 steps."
- "A developer tool needs a pricing page with 3 tiers, a monthly/yearly toggle, and a highlighted team plan."
The tool returns component ideas. Then search for the best one by name and fetch its code.

## What NOT to do
- Don't fetch a component and ship it unchanged (wrong palette, wrong type, wrong copy = slop with a better starting point).
- Don't use a component because it's popular. Use it because it fits the direction, the moment, and the screen's job.
- Don't build a page out of 10 different 21st.dev components with 10 different looks. Pick one visual language and adapt every component to it.
- Don't use a component with fake proof (invented testimonials, fake logos, fake stats). If the component's demo has fake proof, replace it with the product's real content or delete it.
