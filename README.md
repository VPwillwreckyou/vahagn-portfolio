# Vahagn Papikyan — Portfolio

Single-page portfolio site. Static HTML, CSS and JavaScript — no build step, no framework, no backend.

Live: https://vpwillwreckyou.github.io/vahagn-portfolio/

## Structure

```
index.html        the whole site (markup, styles, content, logic)
images/           project screenshots (WebP) + favicons + social preview
images/tech/      technology icons (PNG)
robots.txt        crawler rules + sitemap location
sitemap.xml       sitemap for search engines
vercel.json       security headers for a Vercel deployment (ignored by GitHub Pages)
```

## Run locally

Open `index.html` directly, or serve the folder:

```
npx serve .
# or
python -m http.server
```

## Editing content

* **Text, projects, pricing, contact links** — the `CONFIGS` object near the top of the `<script>` block. It holds three blocks: `en`, `ru`, `hy`. Keep all three in sync when adding a project.
* **Interface labels** (menu, headings, buttons) — the `I18N` object, also per language.
* **Sections** — the `render()` function builds the page from `CONFIGS`.
* **Theme** — `:root` variables at the top of `<style>`; `:root[data-theme="light"]` overrides them for the light theme.
* **Day/night sky** — the `K` (dark) and `KLIGHT` (light) colour ramps, keyed by scroll progress.

A project with `github:""` renders no "GitHub repository" button — used while a repository is private.

## Images

Screenshots are WebP at `images/`. Originals (PNG) stay out of the page to keep loading fast.
`images/og-image.png` is the 1200×630 social preview used by `og:image` / `twitter:image`.
Favicons: `favicon-32.png`, `favicon-64.png`, `favicon-180.png` (Apple touch icon).

## Deployment

* **GitHub Pages** — push to `master`; the site is published from the repository root.
* **Vercel** — import the repository; no build command, output directory `.`. `vercel.json` adds the
  security headers GitHub Pages cannot set.

If the site moves to a custom domain or a Vercel URL, update the absolute URLs in `index.html`
(`og:image`, `og:url`, `twitter:image`, `canonical`), `robots.txt` and `sitemap.xml`.

## Notes

* Fonts: Bricolage Grotesque from Google Fonts; falls back to system fonts offline.
* Content renders with JavaScript. A `<noscript>` block gives visitors and crawlers the basics.
* Verified in headless Chrome: no console errors, no failed requests, all 7 project cards and 25 images load,
  EN/RU/HY switching, dark/light themes, contact dialog, mobile layouts at 320/360/390/768/1440 px.
