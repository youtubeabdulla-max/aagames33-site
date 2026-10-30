# aagames33.com

The AA Games studio website: plain HTML and CSS served by GitHub Pages from the `main` branch,
with the custom domain in `CNAME`. No build step and no JavaScript. For the owner's editing steps see
[HOW_TO_EDIT.md](HOW_TO_EDIT.md).

## Layout

- `index.html`: home page (hero, game cards, About, Help & privacy, contact)
- `<game>/index.html`: one page per game, with its `icon.webp`, `banner.webp`, `share.jpg` (link previews),
  `shot-N.webp` screenshots and a `skins/` folder for upcoming skins
- `assets/style.css`: all styles. Each game page sets `--accent` on `<body>`.
- `assets/fonts/`: Fredoka SemiBold and Nunito (variable), subset to Latin and saved as WOFF2. Both are
  under the SIL Open Font License; the license files are next to them.
- `404.html`, `robots.txt`, `sitemap.xml`, `favicon.ico`, `apple-touch-icon.png`, `assets/logo.svg`, `assets/og.jpg`
- `.nojekyll`: GitHub Pages serves the files as they are

All paths are root-absolute (`/assets/...`), so the site must be served from the domain root.

## Where the images came from

Copied from the game folders in `~/Desktop/AN GAMES/` (those folders were not changed), resized and saved
as WebP. Icons and screenshots match the live App Store listings on 30 Oct 2026.

| Game | Icon | Banner | Screenshots |
|---|---|---|---|
| Carrom Crew | `CARROM_CREW_v1/17_STORE/app_icon_1024.png` | `17_STORE/google_play_feature_graphic_1024x500_v120.png` | `17_STORE/screenshots/apple_6.5in_1242x2688_v120/` |
| Chromo Rush | `15_UNITY_PROJECT/ChromoRush/Assets/Chromo/Icons/app_icon_1024.png` | `17_STORE/google_play_feature_graphic_1024x500.png` | `17_STORE/screenshots/apple_6.5in_1242x2688_v1_1/` (1.1, the live version) |
| RIFT: World Rush | `RIFT/Assets/Rift/Art/RiftIcon-v2.png` | middle slice of the same icon art | `RIFT/StoreAssets/1320x2868-world-*.png` |
| Bonbon Blast | `BonbonBlast/Assets/_Game/Art/AppIcon.png` | `BonbonBlast/Store/Icons/play-feature-graphic.png` | `BonbonBlast/Store/Screenshots/iphone-*.png` |
| ColorLand | `colorland/assets/icon/icon.png` | `colorland/store/graphics/feature_graphic_1024x500.png` | `colorland/deliverables/store_screenshots/iPhone_17_Pro_Max/` |

## Preview and publish (for Claude sessions)

- Preview: serve the folder at the root of a local web server and open it in a browser, for example
  `python3 -m http.server 8433` from this folder, then <http://localhost:8433>. Check phone width (375 px) too.
- Publish: commit to `main` and `git push` (remote `git@github.com:youtubeabdulla-max/aagames33-site.git`,
  SSH; HTTPS pushes stop at a username prompt). Pages rebuilds in about a minute.
- DNS is at Cloudflare and all records are "DNS only" (grey cloud). The website's records: apex `A`
  185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153; `www` CNAME
  `youtubeabdulla-max.github.io`; `_github-pages-challenge-youtubeabdulla-max` TXT (domain verification).
- Records in the zone that are **not** the website's. Never change them from here:
  - game backend: `api` (A, AAAA) and `_acme-challenge.api` (CNAME to Fly)
  - Carrom Crew's own server: `carrom-server` (A, AAAA) and `_acme-challenge.carrom-server` (CNAME to Fly)
  - e-mail (Cloudflare Email Routing, support@aagames33.com forwards to youtubeabdulla@gmail.com):
    3 MX `route1/2/3.mx.cloudflare.net`, apex TXT `v=spf1 include:_spf.mx.cloudflare.net ~all`,
    TXT `cf2024-1._domainkey`. Moves to Google Workspace only when the owner's Workspace setup shows its
    MX step, exactly as Google says.
  - apex TXT `google-site-verification=...` (the owner's Google Workspace verification)
- `app-ads.txt` stays on `youtubeabdulla-max.github.io` (the stores list that address); don't add one here.

## Text to update later

- RIFT: World Rush page (`rift-world-rush/index.html`), feature line "No account, no sign-in, plays offline":
  true today, but RIFT is joining the shared game backend. When RIFT ships accounts / sign-in, change or
  remove that line (check the RIFT store listing at the time for the right wording).
