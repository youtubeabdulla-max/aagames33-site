# How to edit aagames33.com

The website is a set of plain files in this GitHub repository. When you save ("commit") a change on
github.com, the website updates by itself, usually in about a minute. There is nothing to build or install.

## Change some text (the quick way)

1. Go to <https://github.com/youtubeabdulla-max/aagames33-site> (signed in as youtubeabdulla-max).
2. Open the file you want to change (see the table below). For a game page, click the game's folder first,
   then `index.html`.
3. Click the **pencil icon** (Edit this file) at the top right of the file.
4. Change the words. Only change text that sits between a `>` and a `<`, and leave the parts inside `< >` as
   they are. Example: in `<p class="tagline">Flick. Pocket. Cover the Queen.</p>` you change only
   `Flick. Pocket. Cover the Queen.`
5. Click the green **Commit changes...** button, then **Commit changes** in the box that opens.
6. Wait about a minute and open <https://aagames33.com>. If you still see the old text, your browser is
   showing a saved copy: wait a few minutes or open the site in a private window.

## Where things are

| What you see on the site | File to edit |
|---|---|
| Home page (top text, game cards, About, Help & privacy, contact) | `index.html` |
| Carrom Crew page | `carrom-crew/index.html` |
| Chromo Rush page | `chromo-rush/index.html` |
| RIFT: World Rush page | `rift-world-rush/index.html` |
| Bonbon Blast page | `bonbon-blast/index.html` |
| ColorLand page | `colorland/index.html` |
| Page shown for a broken link | `404.html` |
| Colours, sizes, fonts | `assets/style.css` |
| A game's icon, banner, screenshots | that game's folder: `icon.webp`, `banner.webp`, `shot-1.webp`, `shot-2.webp`, ... |
| Upcoming skin pictures | that game's `skins` folder |

Each game's look has its own colour: it is the `--accent: #f5a623` part of the `<body ...>` line near the top
of the game's `index.html`. You can change the colour code there.

## When a game goes live on a store

Do this in **two files**: the home page `index.html` and the game's own `index.html`.

1. Find the line with `Coming soon to` for that store, for example
   `<span class="store soon"><small>Coming soon to</small>Google Play</span>`.
2. Right above it is a note that starts with `<!-- When it is live, replace the next line with:`.
   Copy the `<a class="store" ...>...</a>` part out of that note.
3. Replace the whole `<span class="store soon">...</span>` line with what you copied, then delete the note.
4. If the game had no store at all before, also change:
   - on the home page: `<span class="tag soon">Coming soon</span>` to `<span class="tag out">Out now</span>`
   - on the game page: `<li>Coming soon</li>` to `<li>Out now</li>`
5. Commit, then tap the new button on your phone to check it opens the store.

The store links, ready to use:

| Game | App Store | Google Play |
|---|---|---|
| Carrom Crew | live already | live already |
| Chromo Rush | live already | `https://play.google.com/store/apps/details?id=com.chromorush.game` |
| RIFT: World Rush | live already | `https://play.google.com/store/apps/details?id=com.riftprototype.rift` |
| Bonbon Blast | `https://apps.apple.com/app/id6816154385` | `https://play.google.com/store/apps/details?id=com.angames.bonbonblast` |
| ColorLand | `https://apps.apple.com/app/id6816152811` | `https://play.google.com/store/apps/details?id=com.colorland.app` |

## Add an upcoming skin

1. Get the picture ready: square (about 600 x 600 pixels), PNG, JPG or WebP, ideally under 300 KB.
   Give it a simple name: small letters and dashes, no spaces, for example `gold-striker.png`.
2. On GitHub open the game's folder, then its `skins` folder. Click **Add file** > **Upload files**, drag the
   picture in, and click **Commit changes**.
3. Open the game's `index.html` and click the pencil. Find the **Upcoming skins** section (on Bonbon Blast and
   ColorLand it is called **Coming next**). It has a note with a 4-line example:

   ```html
   <article class="skin">
     <img src="/carrom-crew/skins/gold-striker.png" alt="Gold Striker" loading="lazy">
     <div><b>Gold Striker</b><span>Coming in December</span></div>
   </article>
   ```

   Copy those 4 lines and paste them **under** the note, after its closing `-->`. Change the picture's file
   name, the skin name (it appears twice: in `alt="..."` and in `<b>...</b>`), and the date text.
4. Delete the box that says "New skins are on the way" (the 4 lines that start with
   `<div class="skin-empty">` and end with `</div>`) once your first skin is in.
5. Commit. For more skins, paste more 4-line blocks one under another.

## Replace a screenshot, icon or banner

Upload a new file with **exactly the same name** into the same folder (for example
`carrom-crew/shot-2.webp`): GitHub replaces the old one. If your new picture is a PNG, upload it as
`shot-2.png` and change `shot-2.webp` to `shot-2.png` in the game's `index.html`.
Phone screenshots should be tall (portrait); banners are 1024 x 500.

## Made a mistake?

Nothing is lost: GitHub keeps every version. Open the file, click **History**, open the version from before
your change, copy its text, then edit the file and paste it back. Or ask Claude to undo it for you.

## Ask Claude instead

You can ask any Claude session things like "on aagames33.com, change the Carrom Crew tagline to ..." or
"add this skin to the Chromo Rush page". The files are in `~/Desktop/AN GAMES/aagames33-site`, and Claude
can preview the change, commit it and push it over SSH (see `README.md`).

## Please don't touch

- `CNAME`: it holds `aagames33.com`. Deleting it takes the site off your domain.
- The DNS records at Cloudflare for `aagames33.com`: the four `A` records, `www`, the
  `_github-pages-challenge-youtubeabdulla-max` TXT record, and the `api` records the game server uses.
- `app-ads.txt` does **not** live on this site. It stays at `youtubeabdulla-max.github.io/app-ads.txt`
  because the store listings point to that address. Moving it is a separate, planned change.
