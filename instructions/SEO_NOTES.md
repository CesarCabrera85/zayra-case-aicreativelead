# SEO — Zayra case pages only

Everything here applies ONLY to the two new pages `/work/zayra` and `/es/work/zayra`.
Nothing in the global SEO system changes.

## Files
| File | What it is |
|---|---|
| `seo_meta.json` | title, description, canonical, robots, hreflang, OpenGraph, Twitter, breadcrumbs — per language |
| `schema_work_zayra_en.jsonld` / `_es.jsonld` | JSON-LD `@graph` for each page: CreativeWork · VideoObject · MusicGroup (Zayra) · MusicAlbum · BreadcrumbList |
| `alt_texts.csv` | alt text EN/ES for every web image (by public path) |
| `web/zayra-og-en-1200.jpg` · `web/zayra-og-es-1200.jpg` | OpenGraph images 1200×630 (+ WebP twins) → publish at `/images/work/zayra/` |

## Page metadata (summary)
| | EN `/work/zayra` | ES `/es/work/zayra` |
|---|---|---|
| title | Zayra case: one AI campaign, every format \| AI Creative Lead | Caso Zayra: campaña con IA, una identidad \| AI Creative Lead |
| description | How AI Creative Lead turned one creative direction into a full launch campaign for AI artist Zayra: film, cutdowns, stills and every format, one face. | Cómo AI Creative Lead convirtió una dirección creativa en la campaña completa de la artista IA Zayra: film, reducciones, foto y todos los formatos. |
| H1 (page) | ZAYRA — ENTERA | ZAYRA — ENTERA |
| canonical | https://aicreativelead.com/work/zayra | https://aicreativelead.com/es/work/zayra |
| hreflang | en → /work/zayra · es → /es/work/zayra · x-default → /work/zayra (same set on both pages) | |

## Schema rules
- `creator` / `publisher` point to the EXISTING Organization `{"@id":"https://aicreativelead.com/#org"}`. Do not redefine the organization.
- `VideoObject.uploadDate`: replace `PUBLISH_DATE_ISO8601` with the real publish date (e.g. `2026-10-15`).
- `MusicGroup.sameAs`: Spotify artist + Instagram (verified 06/10/2026). The YouTube music video is attached as `subjectOf`.
- Validate with Google Rich Results Test + Schema.org validator before release.

## Internal links to add (only these)
| From | Where | Anchor (EN / ES) | To |
|---|---|---|---|
| Home `/` and `/es` | new `#featured-case` block | View the full case → / Ver el caso completo → | /work/zayra · /es/work/zayra |
| `/work` and `/es/work` | new "Featured cases" section | View case → / Ver caso → | /work/zayra · /es/work/zayra |
| `/method` and `/es/method` | `section#bibles`, last paragraph | See it in a full campaign: the Zayra case → / Míralo en una campaña completa: el caso Zayra → | /work/zayra · /es/work/zayra |
| `/work/zayra` | closing `nav.related` (same component as /work) | AI series · The 8-stage chain · The studio | /series · /method · /studio (ES equivalents on ES page) |

## Sitemap
If the sitemap is generated from the route list, the two new routes appear automatically — nothing else to do.
If adding them would require editing the SEO engine or `/admin/seo`, DO NOT edit it: report back and César adds them.

## Must NOT change (global)
Home H1 · Home positioning/hero · global metadata · existing URLs/slugs · redirects · robots · global hreflang · global schema
· llms.txt · Search Console · Bing · SerpAPI · existing Analytics · /admin/seo · weekly SEO engine.
