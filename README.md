# OscarYau525.github.io

Personal academic homepage of Chung-Yiu Yau, built with [Hugo](https://gohugo.io/)
(v0.119.0 extended) and the Hugo Blox *Academic CV* theme (Bootstrap v5 module).
Deployed to GitHub Pages by `.github/workflows/publish.yaml` on every push to `main`.

See [env_setup.md](env_setup.md) for installing the toolchain. Day-to-day:

```powershell
hugo server --disableFastRender --navigateToChanged   # local preview at http://localhost:1313/
hugo --minify                                         # production build into public/
```

## How the site is organised

The page has **one source of content** and **several interchangeable visual styles**.
Two menu buttons sit in the top-right corner: **Light/Dark** (Auto = follow the system,
the default; or force Light or Dark) and **Style** (pick a visual style). Both choices
are remembered in the visitor's browser. Switching never changes the content or the
layout, only the stylesheet.

```
content/authors/admin/_index.md     bio, name, social links, avatar.jpg   (content)
data/papers.yaml                    every publication + the filter groups (content)
content/_index.md                   which blocks appear on the homepage, in which order
data/styles.yaml                    registry of visual styles shown in the Style menu
assets/scss/styles/<id>.scss        one stylesheet per style (plain.scss, warcraft.scss, ...)
assets/scss/switcher.scss           shared look/behaviour of the two menu buttons
assets/scss/base.scss               style-independent rules every style needs (filter hide rule)
layouts/partials/pub/card.html      markup of one publication card (shared by all blocks/styles)
layouts/partials/blocks/paper.html            "Publications" block (filter buttons + list)
layouts/partials/blocks/paper_highlight.html  "Highlight" block
layouts/partials/hooks/head-start/style-init.html    sets <html data-style / data-scheme> before CSS loads
layouts/partials/hooks/head-end/site-styles.html     loads fonts, vendor CSS and the style bundle
layouts/partials/hooks/body-end/style-switcher.html  the Light/Dark and Style menu buttons + their JS
static/uploads/                     PDFs, figures, CV
```

### Editing content

* **Add or edit a paper**: edit `data/papers.yaml`. The file documents every field at the
  top. Papers are displayed in file order; `highlight: true` moves a paper to the
  Highlight block. Titles, tldr and captions accept HTML and MathJax (`\(x^2\)`).
* **Add a filter group**: add it to `groups:` in `data/papers.yaml` and reference its id
  from the papers. Styles may give the new group its own tint (optional).
* **Bio / name / social links**: `content/authors/admin/_index.md`.
* **Block titles or order**: `content/_index.md` (`sections:`). Both paper blocks accept an
  optional `content.title`.

### Adding a visual style

1. Add an entry to `data/styles.yaml` (`id`, `label`, `description`, optional `google_fonts`).
2. Create `assets/scss/styles/<id>.scss`. Every rule must be nested inside
   `html[data-style="<id>"] { ... }` so styles cannot leak into each other.
   Use `plain.scss` and `warcraft.scss` as references for the selectors to theme
   (page background, about block, section headings, filter buttons, publication cards,
   group tints, footer, Style menu). The build fails loudly if a registered style has no file.
3. Styles must not change content or layout: no `display: none` on content, no reordering.
   Behavioural rules shared by all styles (the filter hide rule) live in `assets/scss/base.scss`.
4. Light/dark: the visitor's mode is Auto (OS `prefers-color-scheme`), or forced via
   `<html data-scheme="light|dark">`. Write each variant's colours once in a mixin and emit it
   under both the media query (guarded with `:not([data-scheme="..."])`) and the forced
   attribute, as `plain.scss` and `warcraft.scss` do. The theme also toggles `body.dark`.
5. If you make the new style the `default`, also give its top-level selector the alias
   `html:not([data-style])` (see `plain.scss`) so the page is styled when JavaScript is off.

`?style=<id>` on the URL previews a style for that visit (for example
`http://localhost:1313/?style=warcraft`). `?scheme=light` or `?scheme=dark` additionally forces
the light or dark variant of a style for that visit, regardless of the OS preference (the
styles otherwise follow `prefers-color-scheme`).

### Styles included

| id         | What it is                                              |
|------------|---------------------------------------------------------|
| `plain`    | Shown as **Plain** in the menu. The original minimal look; follows the OS light/dark preference. |
| `warcraft` | Shown as **Epic** in the menu. Dark fantasy look inspired by the Warcraft games and their websites. Follows the OS preference: dark stone by default, a parchment "daylight" variant when the OS prefers light. |

## Credits

Theme: [Hugo Blox Academic CV](https://github.com/HugoBlox/theme-academic-cv), MIT licensed
(see [LICENSE.md](LICENSE.md)).
