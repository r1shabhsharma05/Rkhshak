# Art Direction — the idea comes from the subject

Distilled from the tasteskill study of 247 curated gallery sites (One Page Love, Awwwards Sites of the Day). Method in our own words; the study's numbers are cited where used, never re-invented. Use this ref when a page needs a direction that belongs to its subject, not to its category.

## 1. Inventory the subject (before any design)
List 8–12 things that belong to this subject and to no competitor: its name and what the name means; its address, street, neighbourhood, light, weather; its numbers (seats, price, year); the constraint it lives with; its materials and colours; its rituals and hours; the printed things of its world (timetable, label, ticket, sign). The idea comes from this list, not from the category. Each item is also a picture search.

## 2. Write the argument
List the page as claims with their proof, one line per section. The claims decide which sections exist and in what order. Delete any section that has no claim. This is how you avoid the stock sequence of hero, logos, three features, testimonial, pricing, call to action.

## 3. Draw the direction
Deal three directions (idea, composition, type, palette, photographs, section blueprints) and pick the one that can carry something only this subject has — not the most familiar. Adopt it whole; do not blend it with the layout you would have made anyway. Redraw one slot only for a stated reason (contradicts a brand constraint, needs an asset that does not exist). Never redraw to get something more comfortable. When the brand fixes palette or type, take only composition from the deal and map the brand's values onto the roles.

## 4. Find the idea
Fill this sentence from the subject itself, before building:
> On this page, **[something that belongs to the subject]** becomes **[the device the direction calls for]**.
Places to look: its output (put the real output on the page as material), its object or shape, its name, its place, its ritual, its artefact (ticket, menu, label, receipt), its opposite. **Competitor test:** put the nearest real competitor in the sentence. If it still works, the idea belongs to the category, not the subject. "Clean and modern" is not an idea.

**One live thing.** Give the page one thing the visitor can do, or that differs on each visit, made from the idea: pick a material and see the product in it; type a name and see it set in the product's letters; set the figures and read the real result. Rules: it uses the subject's real content, works on a phone with a thumb, has a plain fallback without script, never blocks reading, and it is one thing, not a playground.

## 5. Write the words first
Write the whole page as a copy deck (plain text) before markup. Headlines fit two lines or fewer at every width (about 32 characters is safe at a confident size; the studied heroes have a median of 5 words). One supporting sentence under the headline, shown with it. The first screen answers the visitor's first question in large type. Write the full content — every section delivers its information completely. Thin sections are the commonest reason a clean page loses to a busier one. Proof is never invented: no customers, quotes, reviews, press, logos, or statistics nobody gave.

## 6. Build still, then look, then move
- **Build with motion off in your head.** A page that needs animation to look finished is not finished. Tokens first; hero exactly as the blueprint describes; each section from its blueprint, carrying the idea into every section (pricing, FAQ, footer included — a distinctive first screen followed by stock blocks is the commonest failure).
- **Imagery, in preference order:** the project's own pictures; generated, if an image tool exists; real pictures of the subject's world from open collections (licensed for commercial use, downloaded into the project, credited in the footer, never presented as the subject's own); drawn in code from the subject itself; dealt photographs only where an honestly generic picture fits; type and colour alone. Floor: at least four real pictures on the page, usually six to twelve. SVG drawings do not count toward the floor.
- **Fullness.** One dominant thing per screen and the content it carries. One deliberate rest per page at most. Running text in the full ink at 16px or more. One pair of equal outer margins at every width; every section uses the width the page set up — when text sits in the left half, the right half holds its picture, second column, list, or figure, never nothing. No blank stretch taller than about half a screen. Sections 120–240px apart on desktop. A heading on every section; the page's title in one `h1`.
- **Look (the gate that matters).** Passing a lint/inspector means nothing banned was measured — it does not mean the page is good. Open the screenshots at 1440, 768, and 390px and critique them with the fourteen-pass critique (see `design-self-review.md`): write the critique down, fix the top three problems, look again. Three rounds at most. Judge only the pictures: if a problem is visible in a screenshot, it is real, whatever the code says.
- **Move last.** The motion layer is required and is more than one fade: one signature move, an entrance for the parts of every section (heading, then text, then picture, staggered 60–90ms, rising 16–32px with opacity, triggered once), feedback on every control, one moving picture. Transform and opacity only; every move has a `prefers-reduced-motion` fallback that keeps the content and drops the travel. Content never stays hidden if the script fails.

## House rules (short form — the full list is the Floor in `design-principles.md`)
No eyebrows; no monospace outside real code; no index numbering; no thin rules; no gradients; no shadows on things at rest, no glows; no tiny uppercase letter-spaced labels; no icon-topped feature cards, no rows of identical cards; no glass, no backdrop-blur panels, no floating pill navigation; no emoji, no gradient blobs, no decorative shapes, no fake dashboards of grey bars; no styled accent word in a headline; two typefaces at most, usually one. Fill freed space with scale, full content, a real picture, or a field of flat colour — never with another ornament.

## Laws of the craft (numbers from the study)
- **Type:** two or three sizes do the visible work — one very large, one small, nothing in between. Display tracking −0.02 to −0.05em, leading 0.85–1.05. Text 16–20px, leading 1.45–1.6, 45–75 characters per line. Five sizes is the ceiling. Left-aligned by default; centre at most one moment.
- **Space:** one grid, one pair of tight margins (16–32px). Text blocks share two or three left edges on the whole page. Section gaps clearly larger than gaps inside a section. Each section a different composition from its neighbours; none is a card grid.
- **Colour:** one ground, one ink, one accent. The accent appears on the action and perhaps one other thing. Surfaces separated by a small step in tone, never by a line or a shadow. A section may change the whole field colour; nothing fades into anything.
- **Imagery:** one dominant image beats six small ones. Same crop ratios, same treatment, square corners unless the direction says otherwise. Nothing ever lies on top of a headline or a statement.
- **Components:** buttons flat, one fill colour, square-cornered or fully round, decided once. Navigation: wordmark, three to five plain links, one action, no bar chrome. The footer is a designed close, not a sitemap.

## App screens (different run, same honesty)
A screen people work in (dashboard, admin, settings, inbox) follows its own rules: quiet borders, small labels, and repeated panels are normal there; gradients, glows, icons in tinted squares, rainbow charts, and invented vanity numbers are not. A product site that shows its app builds each shown fragment as a real piece of that app, with real data that adds up and one finding stated. Grey bars and made-up numbers are the weakest picture a software page has.
