# Images

## Optimisation audit (on-page)
**Alt text**: every meaningful image has descriptive alt text naming the subject; decorative images use empty alt. Alt text is read by screen readers and by search engines — keyword-stuffed alt is a failure, not an optimisation.
**File size targets**:
| Category | Target | Warning | Critical |
|---|---|---|---|
| Thumbnails | < 50KB | > 100KB | > 200KB |
| Content images | < 100KB | > 200KB | > 500KB |
| Hero / banner | < 200KB | > 300KB | > 700KB |
**Format**: WebP is the default recommendation; AVIF compresses best where supported; JPEG for photos as fallback; PNG for graphics with transparency; SVG for icons, logos, illustrations. Judge the format actually served (magic bytes and response headers), not the URL extension — a `.jpg` URL can serve WebP, and a CDN can negotiate per browser (`Vary: Accept`).
**Responsive**: `srcset`/`sizes` serving correctly sized images; no 3000px image displayed at 300px.
**Lazy loading**: below-fold images lazy; the LCP image never lazy. Detect the method (native `loading="lazy"`, or a lazy-loader's data attributes) — do not assume from one signal.
**LCP image**: `fetchpriority="high"`; non-LCP images `decoding="async"`.
**CLS prevention**: explicit width/height (or aspect-ratio) on every image, embed, and ad slot so content does not jump.
**File names**: descriptive, hyphenated, keyword-bearing (`keyword-description-widthxheight.webp`), no `IMG_0042.jpg`.
**CDN**: images served from a CDN where the site has one; hotlink-protection error pages flagged as broken images, not as images.

## Generated SEO image assets
When the user asks for an image asset (not a general artwork request), the use case sets the spec:
| Use case | Aspect | Resolution | Notes |
|---|---|---|---|
| OG / social preview | 16:9 | 1K | Clean, professional, text-friendly |
| Blog hero | 16:9 | 2K | Dramatic, editorial |
| Schema image | 4:3 | 1K | Clean, descriptive, ImageObject |
| Social square | 1:1 | 1K | Platform-optimised square |
| Product photo | 4:3 | 2K | White background, studio lighting |
| Infographic | 2:3 | 4K | Data-heavy, vertical |
| Favicon / icon | 1:1 | 512 | Minimal, scalable |
| Pinterest pin | 2:3 | 2K | Tall vertical card |

Generation needs an image tool the user has connected — this skill does not invent one. If none is available, write the brief (subject, composition, text, aspect, alt text, file name) and stop.
**Post-generation checklist**: write descriptive alt text naming the subject; rename to the SEO file-name format; convert to WebP; target under 200KB for heroes, under 100KB for thumbnails; add ImageObject schema where the image is the page's subject; for OG images, confirm the og:image tags point at the new file.
