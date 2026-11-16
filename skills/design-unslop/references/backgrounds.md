# Backgrounds — 22 ways to make designs less flat

A flat background is the default. These 22 techniques add depth and texture — but only when they serve the world and the content. A background that fights the content is worse than a flat one.

## The 22 techniques
| # | Technique | What it is | When to use it |
|---|---|---|---|
| 1 | **Felt texture** | A soft, fibrous, matte texture (like felt cloth). | Warm, tactile, craft-like products. Subtle — the texture is felt, not seen. |
| 2 | **Fluted glass** | Vertical ridges that bend light (like fluted glass panels). | Frosted-glass surfaces, premium/calm interfaces. Keep it behind content, never over it. |
| 3 | **Thermal gradients** | Heat-map colour ramps (cool → warm). | Data, energy, temperature, intensity. The gradient means something (hot/cold), it's not decoration. |
| 4 | **Water ripples** | Concentric ripples, like a drop in water. | Calm, fluid, aquatic products. Subtle and slow — never a distracting animation. |
| 5 | **Speckled graphite** | Dark surface with fine light speckles (like graphite). | Dark, technical, precise products. The speckles add grain without noise. |
| 6 | **Single-hue landscapes** | A landscape rendered in one hue (monochrome scene). | Hero backgrounds where the image is the world, not a photo. One hue keeps it calm. |
| 7 | **Blueprint grids** | Engineering blueprint lines and grids. | Technical, building, planning products. The grid is the material, not a decoration. |
| 8 | **Halftone** | Dots of varying size (print halftone). | Editorial, retro, print-inspired designs. Use for images or as a texture, not for text. |
| 9 | **Grainy gradients** | A gradient with film grain on top. | Any gradient that looks too smooth/digital. Grain makes it feel printed, not rendered. |
| 10 | **Grass texture** | Fine, organic, grass-like texture. | Natural, outdoor, garden products. Keep it quiet — texture, not a photo. |
| 11 | **Dithered images** | Images reduced to a limited palette with dithering (retro pixel). | Retro, lo-fi, playful products. The dithering is the style, applied consistently. |
| 12 | **Paper texture** | Subtle paper grain and fibres. | Editorial, writing, document products. The paper is the world. |
| 13 | **Contour lines** | Topographic contour lines (like a map). | Maps, outdoors, data, exploration. The lines mean elevation — use them where that fits. |
| 14 | **Cloud sky** | Soft, cloudy sky gradient. | Calm, airy, weather products. Keep it light — the sky is the background, not the subject. |
| 15 | **Pixel mosaics** | Small squares forming a mosaic. | Retro, game, pixel-art products. The mosaic is a pattern, not a photo. |
| 16 | **Lens distortion** | Edges bend as if seen through a lens. | Photography, optics, experimental designs. Use sparingly — distortion fights readability. |
| 17 | **Stippled gradients** | A gradient made of tiny dots (stippling). | Print-inspired, editorial designs. Dots instead of a smooth ramp. |
| 18 | **Square-dot grids** | A grid of square dots (not lines). | Technical, precise, modular products. Dots are quieter than lines. |
| 19 | **Blurred photos** | A photo blurred into a soft wash of colour. | Hero backgrounds where the photo's colour matters but its detail doesn't. Blur enough that text is readable. |
| 20 | **Iridescent shapes** | Shapes with shifting, oil-slick colour. | Playful, creative, experimental products. Use one shape, not five — iridescence is loud. |
| 21 | **Impressionist paintings** | Painterly, brushstroke textures (like an Impressionist canvas). | Art, culture, editorial products. The painting is the world. |
| 22 | **ASCII and pixels** | Text characters / pixels as texture. | Developer, terminal, retro products. ASCII is the material. |

## Rules
- **One background per screen.** A screen with a felt texture AND a contour map AND an iridescent shape is three backgrounds fighting. Pick one.
- **Backgrounds are quiet.** The background never competes with the content. If text is hard to read over it, the background is wrong (or needs a scrim/overlay).
- **The background comes from the world.** A paper texture for a writing product, a blueprint grid for a building product, contour lines for a map product. Never pick a background because it looks cool — pick it because it's the world.
- **Working screens stay neutral.** Dashboards, apps, and tools use neutral surfaces. Background techniques belong on landing pages, heroes, and moments — not on a data table.
- **No background that reads as a colour.** A background that is orange/brown/blue/green is a coloured background, not a texture. The technique adds depth, not hue.
- **Performance.** Textures are CSS/SVG, not 2MB images. A background that slows the page is not a background, it's a bug.
- **Reduced motion:** animated backgrounds (ripples, clouds, water) freeze under `prefers-reduced-motion`. The static frame must still look good.
