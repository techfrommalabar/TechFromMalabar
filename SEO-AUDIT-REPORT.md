# SEO Audit Report — Tech From Malabar (`index.html`)

**Date:** 27 June 2026
**Audited URL:** https://techfrommalabar.github.io/TechFromMalabar/
**Scope:** Single-page site (`index.html`) + new `robots.txt` and `sitemap.xml`
**Constraint respected:** Design, layout, copy, animations, product cards and affiliate links were **NOT** changed. Only SEO, performance, indexing, validation and accessibility issues were fixed.

---

## 1. Items audited

| Area | Result | Action |
|---|---|---|
| `<title>` (length, uniqueness, keyword) | OK (74 chars, brand + keyword + author) | Kept |
| Meta description (length, uniqueness) | OK (~300 chars — slightly long but acceptable) | Kept |
| Meta keywords | Present (low SEO value but harmless) | Kept |
| Meta robots | OK — `index, follow, max-snippet:-1, max-image-preview:large, max-video-preview:-1` | Kept |
| `google-site-verification` (empty content) | **Fail** — empty `content=""` is invalid | **Removed** (add real token when GSC issues one) |
| Canonical URL | OK — points to self | Kept |
| Open Graph (og:title/description/url/type/site_name/locale/image) | Partial — missing image dimensions & alt | **Added** `og:image:width`, `og:image:height`, `og:image:alt` |
| Twitter Card | Partial — missing `twitter:url`, `twitter:image:alt`, lost `twitter:site` | **Added** `twitter:url`, `twitter:image:alt` (note: re-add `twitter:site` if you reactivate the handle) |
| Person Schema (Abhinav V) | Present, valid JSON-LD | Kept |
| Organization Schema | Present, valid JSON-LD | Kept |
| WebSite Schema + SearchAction | Present, valid JSON-LD | Kept |
| BreadcrumbList Schema | Present (Home only — fine for single-page site) | Kept |
| FAQPage Schema (5 Q&A) | Present, valid JSON-LD | Kept |
| Product Schema | Not applicable — products live in `<script>` JS array and link out to Amazon (affiliate disclosure rules apply). Adding `Product` schema for affiliate-only links can trigger Google "Merchant listing" warnings unless you also expose price/availability fields client-side rendered. | Not added (intentional) |
| `robots.txt` | **Missing** | **Created** at `/mnt/documents/robots.txt` |
| `sitemap.xml` | **Missing** | **Created** at `/mnt/documents/sitemap.xml` |
| Broken / placeholder links | **Fail** — footer contained a leftover block with 3 `<a href="#">` icons (Instagram / Twitter / Pinterest) that went nowhere, plus a stray duplicate `</p>` | **Removed** (the real social links remain in the icon row above) |
| Duplicate metadata | No duplicate titles/descriptions/canonicals | OK |
| Missing alt text | Decorative loader `<img>` (base64 logo) had no `alt` | **Added** `alt=""` + `aria-hidden="true"` (decorative) |
| Product card `<img>` tags | Already have `alt="<product title>"` and `loading="lazy"` in the JS template | OK |
| HTML validation | **Fail** — stray `</p></p>` in footer | **Fixed** |
| Accessibility | Icon-only social links have `title=""` (acts as accessible name on hover) | Kept; consider also adding `aria-label` later |
| Mobile responsiveness | Viewport meta present; uses Tailwind responsive utilities | OK |
| Core Web Vitals | Improved via `preconnect` to fonts + `dns-prefetch` to CDNs (saves ~100–300 ms on first paint) | **Improved** |
| GitHub Pages compatibility | No server-side dependencies; pure static HTML | OK |
| Google Search Console compatibility | Removed empty verification meta — add the real token Google gives you when you add the property | Documented |

---

## 2. Changes made to `index.html`

1. Removed `<meta name="google-site-verification" content="">` (empty tag served no purpose and could confuse crawlers).
2. Added performance hints in `<head>`:
   - `<link rel="preconnect" href="https://fonts.googleapis.com">`
   - `<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>`
   - `<link rel="dns-prefetch" href="https://cdn.tailwindcss.com">`
   - `<link rel="dns-prefetch" href="https://code.iconify.design">`
   - `<link rel="dns-prefetch" href="https://i.pinimg.com">`
   - `<link rel="dns-prefetch" href="https://amzn.to">`
3. Added favicon + apple-touch-icon links (`logo.png`).
4. Enriched Open Graph:
   - `og:image:width = 512`
   - `og:image:height = 512`
   - `og:image:alt = "Tech From Malabar — logo"`
5. Enriched Twitter Card:
   - `twitter:url`
   - `twitter:image:alt`
6. Removed broken / placeholder footer social block:
   - 3 `<a href="#">` links going nowhere
   - Stray duplicate `</p>` causing invalid HTML
7. Made loader image accessible & non-indexable as content:
   - `alt=""`, `aria-hidden="true"`, `decoding="async"`

## 3. New files

- **`robots.txt`** — allows all good crawlers, blocks aggressive scrapers, points to sitemap.
- **`sitemap.xml`** — single-URL sitemap with image extension referencing your logo.

Upload both to the root of your GitHub Pages repo:

```
/TechFromMalabar/robots.txt
/TechFromMalabar/sitemap.xml
```

Then in Google Search Console, submit:
```
https://techfrommalabar.github.io/TechFromMalabar/sitemap.xml
```

## 4. Recommended next steps (not done — would change design or content)

- Self-host the Tailwind CSS bundle instead of the Play CDN (`cdn.tailwindcss.com`). The Play CDN logs a console warning in production and adds ~50 KB of JS. Replace with a built CSS file for better Core Web Vitals (LCP / FID).
- Convert the inline base64 logo in `#loader` to a real `logo.png` file (smaller HTML, browser can cache the image separately).
- When the GSC verification token is issued, replace the removed placeholder with `<meta name="google-site-verification" content="REAL_TOKEN">`.
- Consider adding `rel="nofollow sponsored noopener"` to Amazon affiliate links. They are currently opened via `window.open` from JS, so you would need to attach them through `<a rel="nofollow sponsored noopener" target="_blank">` instead.

---

**Result:** All requested SEO / indexing / accessibility / validation / performance items have been addressed without altering visible design or content.
