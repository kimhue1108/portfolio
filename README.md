# Nguyễn Thị Kim Huệ — Portfolio (Soft Studio)

Self-contained static site implemented from the claude.ai/design project
**"portfolio/Home - Soft Studio.dc.html"**. The original was a Claude Design
canvas (React `x-dc` runtime, preview-only); this is a faithful 1:1
re-implementation in plain HTML/CSS/JS that runs anywhere — no build step,
no framework, no runtime dependency.

## Files
- `index.html` — the entire site (markup + styles + logic inlined).
- `assets/` — 31 images (portrait, QR, content/zalo/promo/blog/poster/reel covers).

## View locally
Open `index.html` directly, or serve it (recommended, so embeds work):
```bash
cd <this folder>
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy
Upload `index.html` + `assets/` to any static host (Netlify, Vercel, GitHub
Pages, Cloudflare Pages, S3…). No server code required.

## What's inside
- **Bilingual** Vietnamese / English — toggle (🌐) in the nav re-renders all copy.
- **Sections**: hero, marquee, about + animated stats, skills, experience timeline,
  work (masonry galleries → lightbox), video showreel, contact, footer.
- **Contact form** posts to the existing Google Form
  (`docs.google.com/forms/.../1FAIpQLSf...`) via a no-cors POST.
- **"Lumi"** — the floating companion bottom-right: orbits, eyes follow the
  cursor, click for a sparkle burst + quick-nav menu.
- **Embeds** (TikTok / Instagram / Facebook reels) load from the internet —
  blank when offline; they appear once online.
- **Responsive** down to mobile (nav collapses, grids stack, 2×2 stats).
- Respects `prefers-reduced-motion`.

## Editing notes
- All copy + data (experience, skills, work categories, image lists, video
  URLs) live in the `getData()` function near the top of the `<script>` block.
- To add/replace gallery images, edit the `images: [...]` arrays in `getData()`
  and drop the files into `assets/`.
- Hover styles use `data-hover="prop:val;…"`; conditionals/loops are plain JS.
- **Zoom-to-fit:** the design is a ~1280px artboard. `applyZoom()` sets
  `document.documentElement.style.zoom = innerWidth/1280` on screens wider than
  1280 so the whole composition scales up to fill the viewport (instead of
  sitting small in the middle); below 1280 zoom is 1 and the responsive
  breakpoints take over. `window.__zoom` is read by the Lumi mascot to keep its
  coordinates correct under zoom. To change the base width, edit `dw` in `applyZoom`.
