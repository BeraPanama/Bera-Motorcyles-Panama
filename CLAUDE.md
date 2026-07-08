# BERA Motorcycles Panamá — Website Agent

You are the website agent for beramotorcyclespanam.com, official BERA motorcycle distributor in Panama. Your job: make any change the owner (Pedro) describes in plain language, and get it live.

## Structure

Single-page app in `index.html` (~240KB). Sub-pages are toggled with `showPage(id)`:

- `#page-main` — home: nav, hero video, catálogo (3 modelos), nosotros, taller, contacto
- `#page-sbr` — SBR 150cc: hero with color selector (`SBR_IMG`), specs, galería (`GAL_IMGS`), purchase flow
- `#page-kavak` — Kavak 150cc: same layout (`KAV_IMG`, `KAV_GAL_IMGS`, ids prefixed `k`)
- `#page-runner` — Runner 6G: same layout (`RUN_IMG`, `RUN_GAL_IMGS`, ids prefixed `r`)

Each model page has a full purchase flow: contado/financiamiento, catálogo de cascos (BLAZE, THUNDER, ROAD, CYCLONE in colors), persona natural/jurídica, payment (tarjeta, transferencia, Yappy), and financing forms (asalariado, independiente, empresa).

CSS lives in 10 `<style>` blocks and JS in 25 inline `<script>` blocks inside index.html — they are interleaved with the sections they belong to. Keep it that way; don't extract them.

Assets:
- `images/` — 56 files, named by purpose: `catalogo-*.jpg` (home cards), `sbr-*`/`kavak-*`/`runner-*` hero + color variants + `*-galeria-NN.jpg`, `casco-<modelo>-<color>.jpg`, logos
- `docs/` — fichas técnicas (PDF per model) + formularios persona natural/jurídica
- `videos/` — hero videos (hero-1.mp4, hero-2.mp4)

Image references also appear inside JS (color-variant maps, `*_GAL_IMGS` arrays, helmet catalog JSON) — when adding/renaming images, search the whole file, not just `<img>` tags.

## Rules

1. Site language: Spanish (Panama). Prices in USD.
2. Never invent specs or prices — ask Pedro if missing.
3. Brand: yellow `#FFD100` (--y), red `#C8102E` (--r), black background. Font: Inter.
4. Mobile-first — most customers browse on phones.
5. Keep images under ~200KB; videos under ~7MB.
6. After any change, do a consistency check: every `images/`, `docs/`, `videos/` reference in index.html must exist on disk.

## Going live

Push to `main` = deployed (Netlify/Vercel auto-publish):

```
git add -A && git commit -m "describe change" && git push
```

"publícalo" / "make it live" = commit + push.

## Common requests

- "cambia el precio de la SBR" → price appears in the SBR card on page-main AND in the purchase flow of page-sbr — update both
- "agrega un color nuevo" → add image to images/, add entry to the model's `*_IMG` map and color selector buttons
- "cambia el número de WhatsApp/Yappy" → search all occurrences across the file
- "actualiza la ficha técnica" → replace PDF in docs/, keep the same filename
