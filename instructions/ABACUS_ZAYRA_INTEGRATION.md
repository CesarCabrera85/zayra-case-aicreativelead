# INSTRUCTIONS FOR ABACUS.AI
# INTEGRATION OF ZAYRA BUSINESS CASE INTO AICREATIVELEAD.COM

Version 1.0 · prepared 06/10/2026 · owner: César Cabrera Boggio (AI Creative Lead)

> **Scope in one line:** ADD the Zayra case to aicreativelead.com in four places — a Featured Case block on the
> Home, a Featured Cases section on /work, a new page /work/zayra (+ /es/work/zayra), and one contextual link on
> /method. Change nothing else. Deploy to a preview URL first; production only after César approves.


> **FILE LOCATIONS IN THIS DELIVERY (read first).** This repository is already organized for the repository:
> all images are in `public/images/work/zayra/`, all videos in `public/media/work/zayra/`, all specs/data in `instructions/`,
> visual references in `previews/`. Wherever this document mentions package folders such as `01_HOME_FEATURE/web`,
> `03_FULL_CASE/<SECTION>/web`, `SEO/web`, `COPY/`, `ABACUS/` or `_REFERENCE_PROTOTYPE`, it means the same files, now located as above
> (`content_model.json`, `copy.json`, `metrics.json`, SEO files -> `instructions/`; previews -> `previews/home_block_*`, `work_block_*`, `case_page_*`).
> `master/` archive files are not part of this delivery and are not needed.

---

## 1. What the project is

**Zayra — Entera** is AI Creative Lead's first full commercial business case.

- **Zayra** is a Latin virtual artist created and developed with AI by AI Creative Lead (own face, voice and songs).
  She is real on the platforms: debut album *Yo no quiero un hombre tibio* (2026, 8 tracks) on Spotify, an official
  music video on YouTube, and an Instagram profile. Links in `COPY/copy.json → links`.
- **The case:** the complete launch campaign for her new single *Entera* — a :30 master film, :15 and :06 vertical
  cutdowns, campaign photography, key art, stories with CTA, and native versions in 16:9 / 9:16 / 4:5 / 1:1 —
  produced from one creative direction ("one day, five lights": dawn → night).
- **What it must prove to an agency/brand:** brief → creative direction → visual system → identity consistency →
  storyboard → final production → video → iteration → format adaptation → delivery. AI Creative Lead does not
  "make AI images"; it produces a full campaign.
- **Note on "Entera":** it is the new single and is NOT on the released Spotify album. Never write or link "listen to
  Entera on Spotify". The Spotify link is presented as her released album.

The creative is final and approved. **Do not redesign it, regenerate it, re-edit the film, re-crop images or
rewrite the copy.** Use the files and words as delivered.

---

## 2. What we deliver (package contents)

```
ZAYRA_FOR_ABACUS/
├─ README.md                      overview
├─ 01_HOME_FEATURE/               Home block: web/ assets + preview_en.html / preview_es.html (visual reference)
├─ 02_WORK_FEATURE/               /work block: web/ assets + preview_en.html / preview_es.html
├─ 03_FULL_CASE/
│  ├─ HERO/  PROJECT/  CREATIVE_DIRECTION/  CONSISTENCY/  STORYBOARD_FINAL/  ITERATION/
│  │  VIDEO/  FORMATS/  FINAL_CAMPAIGN/     each with web/ (for the site) and master/ (archive only)
│  ├─ METRICS/                    metrics.json + METRICS.md (real figures only)
│  └─ _REFERENCE_PROTOTYPE/en|es/index.html   the finished page, built with the package files
├─ COPY/                          copy.json (single source of truth) + EN/*.md + ES/*.md (readable)
├─ SEO/                           seo_meta.json · schema_work_zayra_en|es.jsonld · alt_texts.csv · OG images · SEO_NOTES.md
└─ ABACUS/                        THIS document · PROMPT_FOR_ABACUS.txt · asset_manifest.json · content_model.json
```

- **web/** = optimized files for the site (WebP + JPG fallback; AVIF for above-the-fold images; H.264 MP4 with
  faststart; posters). **Use only web/ files on pages.**
- **master/** = full-resolution archive (JPG q95, video HQ). Do NOT load on pages. Optional: offer as download/press.
- `ABACUS/asset_manifest.json` lists every file: path in package, width/height, weight, `public_path` (where it
  must be published), use, alt EN/ES.
- `ABACUS/content_model.json` maps every section of every block to its files (public paths, srcset, alt, captions).
  **Build the pages from this file + `COPY/copy.json` + `03_FULL_CASE/METRICS/metrics.json`.**

---

## 3. Where each file goes (publishing)

Copy every file listed in `asset_manifest.json` that has a `public_path`, from its package path to the repo's
public folder, keeping the filename:

| Type | Package location | Publish to (Next.js `public/`) | URL |
|---|---|---|---|
| Images (webp/jpg/avif) | `*/web/*.webp|jpg|avif` + `SEO/web/*` | `public/images/work/zayra/` | `/images/work/zayra/<file>` |
| Video (mp4) | `*/web/*.mp4` | `public/media/work/zayra/` | `/media/work/zayra/<file>` |

All filenames are unique and prefixed `zayra-`. The loop `zayra-loop-16x9-silent.mp4` appears in three folders —
it is the same file; publish once. If the site already serves heavy media from its own CDN/bucket, you may host the
mp4 files there instead — then update the paths consistently everywhere (pages, schema, OG).
Do not publish anything from `master/`, `_REFERENCE_PROTOTYPE/` or `preview_*.html`.

Web weight: ≈86 MB total across all formats/sizes; a visitor downloads only what is visible
(lazy images, `preload="none"` films).

---

## 4. HOME — where Zayra goes

- Insert **one new section** `<section id="featured-case">` **after `section#offer`** ("What an AI production company
  does / 01 / OFFER") and **before `section#how`** ("How you hire an AI production company").
  Logic: first what we sell → then proof we can do it → then how to hire us.
- Visual reference: `01_HOME_FEATURE/preview_en.html` and `preview_es.html` (open locally in a browser).
- Structure (compact, one screen on desktop):
  - Standard Home section header (`.sec-head` with `h2` + `.idx`): h2 "Featured production case", idx "CASE 01 — ZAYRA / ENTERA".
  - Two columns: **left** = silent autoplay loop (`zayra-loop-16x9-silent.mp4`, poster `zayra-home-feature-poster-*`),
    whole media is a link to the case; **right** = kicker, title "ZAYRA" (h3), statement "One identity. One campaign.
    Every format.", one-line body, 3 stats (33 / 16 / 4), three mini proofs (4-face identity strip · storyboard→final
    pair · 9:16/4:5/1:1 trio), live line (Spotify ↗ YouTube ↗ Instagram ↗), CTA button "View the full case →".
  - Mobile: stack (media on top).
- **Language:** the Home switches language with `data-en` / `data-es` attributes on each text node. Use the same
  mechanism as `#offer` and `#how` (all strings for both languages are in `COPY/copy.json → en|es.home_feature`).
  CTA href: `/work/zayra` (EN) and `/es/work/zayra` (ES), following the same language-aware link logic the Home
  already uses for other internal links (e.g. the series link).
- Do NOT touch: Home H1, hero/channel deck, ticker, the order of other sections, any existing copy.

## 5. WORK — where Zayra goes

- On `/work` and `/es/work`, insert **one new section** `<section id="featured-cases">` **right after
  `section.inner-hero`** and **before the schedule** ("The schedule / La parrilla").
- Visual reference: `02_WORK_FEATURE/preview_en.html` / `preview_es.html`.
- Content: section header "Featured cases / CASE STUDIES — 02", then two cards:
  - **Zayra (primary, large, ~63% width):** 16:9 media (`zayra-work-card-*`, optional loop), kicker
    "CASE 01 · GENERATIVE CAMPAIGN SYSTEM", title "ZAYRA — ENTERA", one line, 4 tags (Campaign · Talent consistency ·
    Adaptation · Commercial production), 3 stats (33 / 3 / 4), "View case →" → `/work/zayra`.
  - **Miguel Cartujo (secondary):** existing image `/images/series/miguel-cartujo-episode-1-cover.jpg`, kicker
    "CASE 02 · EPISODIC PRODUCTION", one line, 4 tags (Episodic · Characters · World consistency · Narrative
    continuity), "View case →" → `/series` (ES `/es/series`).
- Leave the existing schedule and the existing "Case: Miguel Cartujo" paragraph section exactly as they are.
- The Work H1, title and description stay unchanged.

## 6. Create `/work/zayra`

New route `/work/zayra` (EN, default). It is a case page under Work — no new taxonomy, no `/case-studies/`.
Build it with the site's inner-page system (same layout shell, master bar, footer, fonts, colours, components).
Section order and content (all strings in `COPY/copy.json → en.case`, assets in `content_model.json → case`,
pixel reference `03_FULL_CASE/_REFERENCE_PROTOTYPE/en/index.html`):

| # | Section (id) | Content |
|---|---|---|
| 1 | HERO `#top` | Full-bleed hero: picture `zayra-hero-wall` (mobile: `zayra-hero-wall-vertical`) + silent loop on top; kicker, **H1 "ZAYRA" + "ENTERA"**, statement, one line, CTAs "Watch the film" (#film) / "Send us the brief" (site booking). Below: **process bar** (Brief · Direction · Identity · Storyboard · Iteration · Film · Formats · Delivery → anchors) and the 4-fact strip |
| 2 | THE PROJECT `#project` | Paragraph + key art (EN/ES versions). **"Zayra, on air"** strip: Spotify (album), YouTube (official music video), Instagram — outbound links `target=_blank rel=noopener` |
| 3 | THE CHALLENGE `#challenge` | Big statement + short paragraph + 3 ticks |
| 4 | CREATIVE DIRECTION `#direction` | 5 chapter cards (06:12 Dawn … 23:33 Night), palette (6 swatches), before (3 night images) → after (6 day images), storyboard sheet (16 frames), 6 continuity rules |
| 5 | IDENTITY `#identity` | 16-image grid (4×4, 2 cols mobile) with captions + statement "ONE IDENTITY. MULTIPLE SHOTS. ONE CAMPAIGN." |
| 6 | STORYBOARD → FINAL `#board` | 4 drag-to-compare sliders (board layer clipped over final; `input[type=range]`, keyboard accessible) |
| 7 | ITERATION `#iteration` | Title **"Change the variable. Keep the campaign."** 6 cards: original · changed · {label, changed, kept}. Vertical cards (colour 4:5, CTA 9:16) use narrower columns |
| 8 | VIDEO `#film` | Master :30 (16:9, `<source media>` 1080p desktop / 720p mobile) + cutdowns :15 and :06 (9:16); `controls playsinline preload="none"` + posters. Line: "Also delivered: Spotify Canvas loop and a silent web loop." |
| 9 | FORMATS `#formats` | 3 rows (Noon / Night / Dawn) × 4 native formats with use labels + 7-step campaign system strip |
| 10 | FINAL CAMPAIGN `#campaign` | 24-image masonry gallery, no text |
| 11 | PRODUCTION RESULT `#result` | 8 figures from `metrics.json → full_case` (stats component) |
| 12 | COMMERCIAL CONCLUSION `#proves` | One big sentence + 3 short cards |
| 13 | CTA | The site's existing closing component (`section.closing` + `.btn-red` + `nav.related`) exactly as on /work — same href, same form. Footnote: AI disclosure line |

Rules: H1 is "ZAYRA — ENTERA" (one H1). Section titles are H2. Images: `<picture>` (AVIF if provided → WebP srcset →
JPG `<img>` with width/height, `loading="lazy" decoding="async"` except the hero which is `fetchpriority="high"`).
Respect `prefers-reduced-motion` (no autoplay loop, show poster). The reveal-on-scroll effect, if used, must reveal
anything already above or inside the viewport (anchor jumps must never leave a section invisible).

## 7. Create `/es/work/zayra`

Same page, same components, Spanish strings from `COPY/copy.json → es.case`, ES key art (`zayra-keyart-es-*`),
ES OG image, `lang="es"`, canonical `/es/work/zayra`. Route follows the existing i18n system (`/es/work` already
exists). Language toggle in the master bar links EN ⇄ ES between the two case URLs.

## 8. Link from METHOD

On `/method` (and `/es/method`), in `section#bibles` ("Brand bibles / Biblias de marca"), add ONE paragraph inside
`.prose`, after the existing paragraph that links to the series:

- EN: `<p><a href="/work/zayra">See it in a full campaign: the Zayra case →</a></p>`
- ES: `<p><a href="/es/work/zayra">Míralo en una campaña completa: el caso Zayra →</a></p>`

Same link style as the existing series link. Nothing else changes on /method.

## 9. Components to reuse (do not invent new design)

Reuse what the site already has, in this priority:
- Shell: master bar, footer, fonts (Barlow Condensed / IBM Plex Mono / Archivo), colour tokens, grain overlay.
- Inner pages: `section.inner-hero` pattern, `.sec-head` (h2 + `.idx`), `.lead`, `.prose`, `.tag`, `.btn` / `.btn-red`,
  `section.closing` + `nav.related`.
- From `/series`: `.case` layout, `.stats`/`.stat` (figures), `.gallery figure/figcaption`, `.solve` list, `.mini-link`.
- Only where no equivalent exists (compare slider, iteration cards, format matrix, identity grid, chapter cards,
  "on air" strip, process bar), port the styles from `_REFERENCE_PROTOTYPE` (inline `<style>` there) into the site's
  stylesheet, scoped under a page class (e.g. `.zayra-page`) so nothing global changes.
  Tokens used: bg `#060606`, ink `#ededE8`, lines `rgba(255,255,255,.13)`, accent for this case `#ff2d9b`
  (the site's SOCIAL channel colour). No rounded corners, no shadows, 1px borders.

## 10. Content to keep exactly

- Every string in `COPY/copy.json` (EN and ES) — no rewriting, shortening or "polishing".
- Every number from `metrics.json` — no rounding, no extra figures, no "estimated" numbers. Production hours are
  deliberately NOT published.
- The AI disclosure footnote on the case page.
- The four external links (Spotify album, Spotify artist in schema, YouTube video, Instagram).
- Image crops and order as in the content model / prototype.

## 11. Metadata to add (only on the two new pages)

From `SEO/seo_meta.json`: `<title>`, `meta description`, canonical, `robots index,follow`, hreflang (en / es /
x-default), OpenGraph (`og:type=article`, image 1200×630, video), Twitter card. JSON-LD from
`SEO/schema_work_zayra_en.jsonld` / `_es.jsonld` (replace `PUBLISH_DATE_ISO8601`). Alt texts from
`SEO/alt_texts.csv`. Breadcrumb UI optional; BreadcrumbList schema required. Use the same Next.js metadata
mechanism the other pages use (e.g. `generateMetadata` / page `metadata`), not hard-coded `<head>` hacks.
Sitemap: see `SEO/SEO_NOTES.md` (only if auto-generated from routes).

## 12. Events to measure (reuse the existing GA4 / gtag setup)

The site loads GA4 (`gtag`, consent mode). Send these through the **existing** gtag/dataLayer helper the site
already uses. Do not add a new analytics tool, do not change consent, do not rename or alter `generate_lead`
(the booking form keeps firing it exactly as today).

| Event | When | Params |
|---|---|---|
| `view_zayra_case` | /work/zayra or /es/work/zayra loads | `lang` |
| `view_zayra_home_feature` | Home block ≥50% visible, once per pageview | `lang` |
| `play_zayra_master` | first `play` of the :30 master | `lang`, `quality` (1080p/720p) |
| `play_zayra_cutdown` | first play of a cutdown | `length` (15 / 6) |
| `view_zayra_consistency` | `#identity` ≥50% visible, once | `lang` |
| `view_zayra_storyboard` | `#board` ≥50% visible, once | `lang` |
| `view_zayra_formats` | `#formats` ≥50% visible, once | `lang` |
| `zayra_cta_click` | click on any Zayra CTA | `location`: home_feature · home_media · work_card · method_link · case_hero · case_closing |
| `zayra_outbound_click` | Spotify / YouTube / Instagram link | `destination`: spotify · youtube · instagram |

## 13. Assets to use (by section)

Exact list with public paths, sizes and alts: `ABACUS/content_model.json`. Summary:
Home → `01_HOME_FEATURE/web/*` · Work → `02_WORK_FEATURE/web/*` · Case → `03_FULL_CASE/<SECTION>/web/*` ·
OG → `SEO/web/zayra-og-en|es-1200.jpg`. Films: `zayra-master-30-16x9-1080p.mp4` (5 Mbps), `-720p.mp4` (2 Mbps),
`zayra-cutdown-15-9x16-1080x1920.mp4`, `zayra-cutdown-06-9x16-1080x1920.mp4`, loops `zayra-loop-16x9-silent.mp4`,
`zayra-canvas-9x16-silent.mp4`. Do not re-encode, re-crop or upscale; if your pipeline (e.g. next/image) creates
extra sizes from the JPG/WebP, keep quality ≥ 80 so faces stay clean.

## 14. What you must NOT touch

- Home H1, Home hero/channel deck, Home positioning and existing sections/copy.
- Global metadata, existing titles/descriptions, existing URLs and slugs, redirects, robots.txt, global hreflang,
  global schema (Organization), llms.txt.
- Search Console, Bing Webmaster, SerpAPI, existing Analytics configuration, consent banner, `generate_lead`.
- `/admin/seo` and the weekly SEO engine.
- Main navigation: do NOT add "Zayra" as a menu item. Zayra lives under Work.
- Any other page, component or dependency not listed in this document.
Only ADD Zayra.

## 15. Responsive check

Test at 375 × 812, 768 × 1024, 1280 × 800 and 1440 × 900, EN and ES:
- `document.documentElement.scrollWidth === window.innerWidth` on every page (no horizontal scroll).
- Home block stacks on < 1000 px; Work cards stack on < 1000 px; case grids: identity 2 cols, chapters 2 cols,
  formats 2 cols, sliders 1 col on mobile.
- Hero H1 fits without overflow at 375 px; sticky master bar does not cover section titles after anchor jumps
  (`scroll-margin-top`).
- Compare sliders work with touch and keyboard.

## 16. Video check

- All mp4 return 200 with `Content-Type: video/mp4` and support HTTP range requests (seeking works).
- Loops: `autoplay muted loop playsinline`, play on iOS Safari and Android Chrome; paused/poster under
  `prefers-reduced-motion`.
- Films: `preload="none"`, posters visible, controls work, sound on master and cutdowns, mobile gets the 720p source.
- No video downloads before the user presses play (check Network tab).

## 17. Link check

- Home CTA → /work/zayra (EN) and /es/work/zayra (ES). Work cards → /work/zayra and /series (+ ES). Method link →
  /work/zayra (+ ES). Case process-bar anchors scroll to each section. EN⇄ES toggle swaps between the two case URLs.
- Closing CTA opens the existing booking (`#book`) exactly like /work.
- Outbound: Spotify, YouTube, Instagram open in a new tab, `rel="noopener"`.
- Crawl both case pages: no 404s on images, video, fonts.

## 18. SEO check

- View source on both case pages: one H1, correct title/description, canonical self-referencing, 3 hreflang tags,
  OG + Twitter tags, JSON-LD valid (Rich Results Test, Schema validator), every `<img>` has a non-empty alt.
- Home, /work, /method: title, description, canonical, hreflang and H1 are **byte-identical** to before deploy
  (diff the `<head>` before/after).
- robots.txt, llms.txt, global schema unchanged (diff). Lighthouse on /work/zayra: SEO ≥ 95, Accessibility ≥ 90,
  Performance ≥ 80 mobile (LCP image is the hero picture).

## 19. Analytics check

- GA4 DebugView: each event in §12 fires once with the right params; `page_view` still fires on all pages.
- Submit the booking form on preview: `generate_lead` fires exactly as before (name and params unchanged).
- With consent declined, events follow the site's existing consent behaviour (no change).

## 20. After deployment — verify nothing broke

1. Deploy to a **preview/staging URL** first. Send César the preview link. Production only after his OK.
2. On production: open `/`, `/es`, `/work`, `/es/work`, `/method`, `/es/method`, `/series`, `/work/zayra`,
   `/es/work/zayra` → all 200, no console errors.
3. Home: H1 and hero unchanged; the new block sits between OFFER and HOW; all other sections in the same order.
4. Diff `<head>` of Home, /work, /method against the pre-deploy snapshot: only differences allowed = none.
5. Re-run §15–§19 on production. Check the sitemap (if auto-generated) contains the two new URLs and nothing else changed.
6. Report back with: preview URL, production URL, screenshots (375 / 1440, EN / ES) of the three blocks and the
   case page, Lighthouse scores, and the GA4 DebugView capture.
