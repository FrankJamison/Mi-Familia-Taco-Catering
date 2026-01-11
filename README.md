# Mi Familia Taco Catering (2015)

Static marketing site for **Mi Familia Taco Catering** (multi-page brochure site). Built as classic `.htm` pages with an Artisteer-generated theme, plus light JavaScript for navigation behavior and a photo gallery slider.

This repo is a good “small-but-real” example of shipping a complete website: consistent navigation across pages, a conversion flow (quote request), SEO meta tags, and a light sprinkle of unobtrusive JavaScript.

## Highlights (design + development)

- **Cohesive theme + layout system**: two-column layout with reusable “sheet” components, headers, and menu blocks (see `art-*` classes throughout the markup).
- **Conversion funnel**: `catering.htm` → `quote.htm` form → `thankyou.htm` / `error.htm` redirect flow.
- **Photo gallery UX**: slider-based gallery using **Jssor Slider** with responsive resizing logic (`jssor_1_slider_init()` in `gallery.htm`).
- **Progressive enhancement**: the site works as plain HTML/CSS; JS mainly enhances menus (active state/hover behavior) and the gallery.
- **Modernized baseline (2026 refresh)**: HTML5 doctype + viewport meta, improved responsive behavior, and no jQuery requirement.
- **SEO basics**: per-page `<title>`, and descriptive `meta` tags (description/keywords).

## Tech stack

- HTML: **HTML5**
- CSS: Artisteer v3 theme output (design by Artisteer; development updates by Frank Jamison)
- JavaScript:
  - `js/script.js`: small vanilla JS enhancements (menu separators, vmenu “active” state)
  - `js/jssor.slider.mini.js`: image slider library for the gallery

## Site map

- `index.htm` — Home / welcome copy
- `stand.htm` — Taco stand menu and hours
- `catering.htm` — Catering overview + link to quote request
- `quote.htm` — Catering packages + “Request a Quote” form
- `gallery.htm` — Photo gallery (Jssor slider)
- `about-us.htm` — About copy
- `contact-us.htm` — Phone numbers + email link
- `thankyou.htm` — Confirmation page after quote submission
- `error.htm` — Error page if submission fails

## Run locally

You can open `index.htm` directly in a browser, but using a local static server avoids file:// restrictions and is closer to production behavior.

### Option A: Python

```bash
python -m http.server 8000
```

Then visit `http://127.0.0.1:8000/index.htm`.

### Option B: Node

```bash
npx http-server -p 8000
```

Then visit `http://127.0.0.1:8000/index.htm`.

## Quote form behavior

The quote form on `quote.htm` posts to a hosted form handler:

- Endpoint: `http://www.powweb.com/scripts/formemail.bml`
- Required fields are configured via hidden inputs (`required`, `order`)
- Recipient is set via hidden input (`my_email`)
- Redirects to live URLs on success/failure (`thankyou_url`, `error_url`)

When running locally, submitting the form will still attempt to post to that external endpoint.

## Deployment

This project can be deployed to any static host (traditional hosting, S3, Netlify, etc.).

- Upload the entire folder (relative paths assume `css/`, `js/`, `images/`, `photos/` remain intact).
- Ensure the host serves `.htm` files as HTML.

## Developer notes / maintenance

- **Navigation is duplicated** in the markup (top menu `ul.art-menu` + sidebar menu `ul.art-vmenu`). When changing nav items, update both on each page.
- **Gallery images** are hard-coded in `gallery.htm` as `<img data-u="image" src="photos/...">` entries.
- `js/script.js` is intentionally minimal and runs on `DOMContentLoaded`.

## 2026 refresh notes

- Markup updated to HTML5 + viewport meta.
- Legacy IE6/IE7 shims removed.
- jQuery removed (theme behavior is now vanilla JS).
- Added responsive layout improvements (the theme is fixed-width by default).
