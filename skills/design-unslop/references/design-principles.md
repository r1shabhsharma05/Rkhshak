# Design Principles — the Floor, house rules, and laws of craft

## The Floor (Hallmark — hard rules, never waivable)
Binds every output in every harness, even when nothing else is read.
1. Every colour and every font goes through a token declared at `:root` (or a declared theme block). No literal colour or `font-family` past the token block.
2. Never `transition: all`. Never animate `width`, `height`, `top`, or `left`.
3. Never one italic word inside a roman heading.
4. `overflow-x: clip` on both `html` and `body`. Never `hidden`, never `100vw`.
5. Image-bearing grid tracks use `minmax(0, 1fr)`; display heads carry `overflow-wrap: break-word; min-width: 0`.
6. Every interactive element has `:focus-visible`, appearing instantly.
7. Every animation has a `prefers-reduced-motion: reduce` fallback, and content is visible with scripting off.
8. Never an invented metric, testimonial, logo wall, or case-study count.
9. Never an eyebrow, and never a label in tracked capitals or small caps: labels, captions, table heads, tags, and nav links are the body face (or the theme's label face), a step smaller, sentence or lower case, untracked.
10. Never middle-dot-joined meta strings, arrows glued to link text, or decorative status dots.
11. Never a purple-to-blue gradient, a card inside a card, an emoji as an icon, or a hand-drawn browser or OS window.
12. The hero's headline, one sentence, and primary action are all visible at 1280×800 without scrolling.
13. About 80 words on any one screen; the hero's text is the headline, one sentence, and its actions.
14. The container is capped and centred: at 1920 the gutters grow, the measure and the grids do not.
15. The first non-empty line of the CSS source is the Hallmark stamp, then the critique line, then any waivers.
16. Run a linter/sweep before handoff. Fix every FAIL; fix or waive every REFLEX.

Above the Floor, a **Reflex** is a default a model falls into (waivable on the record with a real reason), and a **Finish** check is craft detail (answered, never blocking).

## House rules (design-taste)
- **Material first.** The page shows the real thing: the user's pictures, screenshots of the real product, the product built at full fidelity, or library photographs — big, in the theme's treatment, each credited in the footer. Pictures take at most a third of the page below the hero, never two photograph-led sections in a row.
- **One idea per screen, set big.** Hero: a headline of seven words or fewer (50 characters), one sentence of twelve words or fewer, one or two actions. Six to nine sections, hero and footer included. 450 visible words at most.
- **Show, do not describe.** Never a stock-site URL, a drawn illustration, an empty wash, a row of counting marks, or an invented figure.
- **Page invariants:** one primary button style, one container width, one column gap below the hero, one radius per nesting level, never more centred heading groups than left-aligned ones.
- **Type:** two families at most (three with one outlier role); body 16px or more; heads one weight and one colour. Labels never mono unless mono is the material.
- **Controls:** eight states on every control; `transform` and `opacity` only; one reveal at most, none where the theme keeps still, visible by default.
- **Fullness comes from scale and pictures, never from more words.**

## Laws of the craft
- **Subtract first.** Agents add. Walk every element and ask: what breaks if this is gone? "Nothing" means delete. Deletions expose each other — walk twice.
- **Slop spreads richness over the chrome; craft keeps the chrome quiet and spends it on one moment.** Working screens people stare at keep neutral surfaces; color lives in the content.
- **One bright element.** Each screen has one polished thing that carries the color and the craft. Everything around it is quiet, so it reads instantly.
- **Quiet chrome.** Navigation, buttons, and text use the tinted neutrals and one accent. Nothing glows, nothing competes with the bright element.
- **A clear idea.** You can say in one sentence what the visual shows and why it belongs to this product.
- **Text on calm space.** The headline sits on a part of the image or layout left empty for it, short and specific, with one primary and one secondary action and nothing stacked under them.
- **Real product, real material.** Previews look like the real app with plausible data, and objects look like real things with weight, light, and shadow.
- **Honor the object.** If you borrow a real thing, it must behave like one: paper doesn't fade, a lock's pins move the right way, and you don't write your reply on the letter you received.
- **Materials must earn themselves.** Frosted glass needs something meaningful behind it. Refraction needs a subject to bend. Liquid metal, chrome, and glossy 3D are AI defaults when abstract — allowed only when the object means something in this product.
- **Texture is optional.** At most one layer, only to fix a named problem (e.g. a gradient that bands). Grain for warm physical worlds, halftone over soft photographic color, topographic lines for terrain/routes/data, concentric rings for one focal object, fluted glass when something high-contrast sits behind it.
