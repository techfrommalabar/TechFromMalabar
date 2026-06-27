# CHANGELOG

All notable SEO / performance / accessibility / indexing changes to **Tech From Malabar** (`index.html`).
Design, layout, copy, animations, product data and affiliate links are unchanged.

## [2026-06-27] — SEO, Performance, Indexing & A11y audit

### `index.html`

**Removed**
- Empty `<meta name="google-site-verification" content="">` (invalid empty content).
- Broken duplicate footer block containing three placeholder `<a href="#">` icon links (Instagram / Twitter / Pinterest) and a stray duplicate `</p>` tag that broke HTML validation.

**Added — head / metadata**
- `<link rel="preconnect" href="https://fonts.googleapis.com">`
- `<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>`
- `<link rel="dns-prefetch" href="https://cdn.tailwindcss.com">`
- `<link rel="dns-prefetch" href="https://code.iconify.design">`
- `<link rel="dns-prefetch" href="https://i.pinimg.com">`
- `<link rel="dns-prefetch" href="https://amzn.to">`
- `<link rel="icon" type="image/png" href="logo.png">`
- `<link rel="apple-touch-icon" href="logo.png">`
- `<meta property="og:image:width" content="512">`
- `<meta property="og:image:height" content="512">`
- `<meta property="og:image:alt" content="Tech From Malabar — logo">`
- `<meta name="twitter:url" content="https://techfrommalabar.github.io/TechFromMalabar/">`
- `<meta name="twitter:image:alt" content="Tech From Malabar — logo">`

**Modified — accessibility**
- Loader `<img>` (base64 logo) now has `alt=""`, `aria-hidden="true"`, `decoding="async"` so it is correctly treated as decorative.

### New files

- **`robots.txt`** — allows all major search crawlers, blocks known aggressive scrapers (AhrefsBot, SemrushBot, MJ12bot), points to the sitemap.
- **`sitemap.xml`** — minimal sitemap with the homepage URL and the logo via the image sitemap extension.
- **`SEO-AUDIT-REPORT.md`** — full audit report with every check and its status.

### Not changed (intentional)

- Design system, colors, fonts, animations, hero, product cards, modals, footer copy.
- Person / Organization / WebSite / BreadcrumbList / FAQPage JSON-LD (already valid).
- Product data array — no `Product` JSON-LD added, because all items are affiliate links to Amazon; adding `Product` schema without authoritative price/availability fields can trigger Search Console "Merchant listing" errors.
- Tailwind Play CDN (`cdn.tailwindcss.com`) and Iconify CDN — replacing them with a self-hosted build would change the design pipeline.
