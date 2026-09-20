# ezana.ai

The marketing site for **Ezana** — an applied-AI firm building decision-support systems
for enterprises and governments in Tanzania and across Africa, deployed on sovereign
infrastructure.

Two pages. No framework, no build step, no JavaScript.

```
index.html        the one-pager: hero, what we build
philosophy.html   the essay, on its own shareable URL
styles.css        the whole design system
netlify.toml      deploy config: no build, publish the root
favicon.svg       the mark, simplified for tab size
logo.svg          the Ezana mark, standalone (the header inlines its own copy)
og.png            1200×630 social card
og.svg            source for og.png
fonts/            Inter + IBM Plex Mono, latin subsets, self-hosted (OFL)
_headers          cache headers for Cloudflare Pages
```

## Working on it

There is nothing to install and nothing to compile. Open `index.html` in a browser, or
serve the directory if you want absolute paths (`/styles.css`, `/fonts/…`) to resolve:

```bash
python3 -m http.server 4400   # then open http://localhost:4400
```

Edit the HTML directly — the copy lives in the markup, not in a data file, because there
are only two pages of it.

## Deploying

Point Cloudflare Pages (or GitHub Pages) at the repository root with **no build command
and no output directory**. Every file is already the file that ships.

If you use GitHub Pages, delete `_headers` — it only means something to Cloudflare.

## Design system

Everything lives in the `:root` block of `styles.css`.

| Token | Value | Use |
|---|---|---|
| `--paper` | `#FCFBF8` | the one surface; there is no dark mode |
| `--ink` | `#111418` | all primary text |
| `--soft` | `#6B7280` | secondary text and mono metadata |
| `--line` | `#E5E2DA` | link underlines at rest |
| `--amber` | `#E8A020` | the accent — wordmark dot, `#` in section kickers, link underline on hover, and nothing else |

Type is Inter for everything visible and IBM Plex Mono for labels, section kickers,
numbering, the byline and footer meta. Body is 17.5px/1.7.

**Width.** The document column (`--column`) is 760px and the reading measure
(`--measure`, 36rem ≈ 66 characters) sits inside it, so a line of prose never outruns
the eye. Only the numbered rows and the three offerings use the column's full width.

Rules worth keeping if you extend the site:

- **No rules.** There is not one horizontal line on the site. Whitespace does all the
  separating — sections, columns, the footer. If something needs dividing, give it more
  room rather than a border.
- **No transitions, no scroll reveals, no parallax.** The only moving thing is the hero
  figure, and it stops for reduced motion. Hover changes an underline colour; that is
  the whole interaction vocabulary.
- **Amber in tiny doses.** Never a fill, never a button. If it starts to look like a
  brand colour, it is being overused.
- **Nothing is a photograph.** Every mark on the site is type or a line drawing, so
  there is no image with its own background to reconcile against the paper.
- **No cards.** The three-column section is text and an image, with nothing drawn
  around them.
- **"judgement"** keeps its e, everywhere.
- Headings are 550–600 weight, not 700. The page should read as a document, not a pitch.

## The favicon

`favicon.svg` is the Ezana mark redrawn for 16px, not the full logo scaled down. The
logo's two swooshes taper to points that disappear below roughly 40px, so the icon keeps
one, thickened, and lets it overhang the ring on both sides - that overhang is what
stops it reading as a plain "O" in a tab. Tested at 16, 32 and 64px before choosing
between four candidates.

The cream ground is deliberate. A transparent icon with an ink mark would disappear
against a dark browser theme; the cream tile keeps it legible either way and matches the
site.

SVG only, no PNG fallback - Chrome, Firefox, Edge and Safari 16+ all render SVG
favicons. Add a 32px PNG beside it if you need to support older Safari.

## The hero figure

The hero animation is **inline SVG**, not a video: two sets of thin ellipses, each
progressively rotated, counter-turning at 54 s and 38 s so they drift through each other
into a slow moiré. It lives in `index.html`, styled by `.ring-set` in `styles.css`.

It replaced a 2.9 MB greyscale clip, which is worth recording because the reason was not
weight. The clip was a 3D render on a mid-grey backdrop carrying a vignette that
**brightened and dimmed as the form moved**, so it read as a grey rectangle sitting on
the cream page. Lifting the white point at encode time and dropping it out with
`mix-blend-mode: multiply` got most of the way there, but a single white point cannot
clip a backdrop whose brightness changes frame to frame, so in some frames the box came
back. Feathering the edges hid the boundary but not the tone. Keying it to transparency
would have eaten the soft contact shadows, which share tones with the form itself.

The lesson, if a moving hero is ever revisited: **any raster clip carries its own
background, and on a coloured page that background is the problem.** Draw it instead, or
source line art with real transparency (SVG, or a Lottie file) — never an MP4, which
cannot carry an alpha channel in any format every browser supports.

Drawn instead, it is about 4 KB rather than 2.9 MB, needs no poster frame or fallback,
stays crisp at any size, has no colour to strip, and cannot have an edge because there is
no image. Under `prefers-reduced-motion: reduce` it simply stops.

## The section drawings

The three offerings are line drawings, inline SVG in `index.html`, styled by `.dwg` in
`styles.css` - the same ink as the hero figure and the type, on transparent ground:

| | |
|---|---|
| 01 Private AI infrastructure | stacked planes - layered capacity, held together |
| 02 Governed model deployment | a lineage graph, one path traced in amber back to source |
| 03 AI agents you can trust | a route through checkpoints, one held open with a line up to a person |

They replaced three JPEGs (a dark 3D render and two black-on-white marks) that never sat
together: on cream paper the row read as one black tile beside two white ones, and no
filter fixed that without changing the artwork. Drawn instead, they have no tile and no
edge, cost about 1 KB each, and each carries a single amber accent doing real work - the
traced path, the checkpoint held open.

Stroke classes: `.l1` `.l2` `.l3` for weight and opacity, `.n` for nodes, `.mk`/`.mkf`
for the amber accent, `.dash` for dashed. They are static by design; the hero is the
only moving thing on the site.

The offerings sit in editorial rows (`.stack`) rather than three columns - drawing left,
text right, each getting the full measure. Titles fit on one line there, which they did
not at a third of the width.

## Measured

Lighthouse scores 100 on performance, accessibility, best practices and SEO on both
pages, measured against a server that gzips, sets cache headers and honours Range
requests the way the host will. First contentful paint 0.8 s, largest contentful paint
1.7 s, CLS 0.

Total page weight is about **80 KB**, nearly all of it the two fonts. There are no
images and no video on the site at all — only `favicon.svg` and the `og.png` social
card, which a browser never loads with the page.

## Before launch

One placeholder is marked with a `PLACEHOLDER` comment in the HTML:

- **The essay byline** — `Imani · Cofounder`. Confirm the name and title. The read time
  and word count (3 min, 622 words) are computed from the text; recompute them if the
  essay changes.

## Regenerating the social card

`og.png` was rendered from an SVG rather than drawn by hand, so it can be rebuilt:

```bash
qlmanage -t -s 1200 -o . og.svg      # renders to a 1200×1200 PNG
sips -c 630 1200 og.svg.png --out og.png
```

The source SVG is authored 1200×1200 with the artwork in the centre band, because
`qlmanage` pads its output to a square and `sips` then crops back to 1200×630. Keep
`og.svg` next to this README if you plan to change the card.
