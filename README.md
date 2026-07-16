# Wish Counter

A single-page, self-contained Genshin Impact wish (gacha) tracker. Import your wish history straight from HoYoverse's API, track pity and 50/50 outcomes, keep a roster of characters and weapons, and view a full banner/event timeline — all stored locally in your browser, no backend required.

**[Live demo →](https://your-username.github.io/your-repo/wish-counter.html)**
*(replace with your actual GitHub Pages URL once deployed)*

![status](https://img.shields.io/badge/status-active-brightgreen) ![no backend](https://img.shields.io/badge/backend-none-blue) ![license](https://img.shields.io/badge/license-MIT-lightgrey)

## Features

- **Wish import** — paste the wish-history URL (grabbed via a one-line PowerShell command while Genshin is open) and pull your full Character Event, Weapon Event, and Standard banner history directly from HoYoverse's API.
- **Pity & 50/50 tracking** — current pity toward 5★/4★, guaranteed-next indicators, win/loss rate on limited banners, and per-pull pity history.
- **Characters & Weapons rosters** — track ownership, constellations, and refinements. Import your real roster from HoYoLAB or a [GOOD-format](https://frzyc.github.io/genshin-optimizer/#/doc) export (Genshin Optimizer, Akasha, etc.).
- **Timeline** — a Gantt-style chart of character/weapon banners and in-game events, built from HoYoLAB's `act_calendar` data, with countdowns and custom banner titles.
- **Pull History chart** — monthly breakdown of 5★/4★/3★ pulls.
- **Multiple accounts**, **local backup export/import**, and compatibility with old **paimon.moe** backups.
- **100% client-side** — all data is stored in your browser's `localStorage`. Nothing is ever sent to a server other than HoYoverse/HoYoLAB (for importing) and paimon.moe (for hotlinked character/weapon art).

## Getting started

### Option 1: Use it via GitHub Pages
Just open the [live demo](#wish-counter) link above — no installation needed.

### Option 2: Run it locally
1. Clone or download this repo.
2. Keep `wish-counter.html`, `styles.css`, and `script.js` in the same folder.
3. Open `wish-counter.html` in any modern browser.

There's no build step, no dependencies, and no server — it's plain HTML/CSS/JS.

## How to import your wishes

1. Open **Import Wishes** in the app.
2. Copy the PowerShell command shown in the modal.
3. Open Genshin Impact and go to the in-game **Wish History** screen.
4. Run the copied command in PowerShell (on the same PC as the game). It generates a temporary wish-history URL and copies it to your clipboard.
5. Paste that URL into the app and click **Fetch Wishes**.

Re-running an import only fetches new wishes since your last import — nothing is duplicated or lost.

### Importing your roster / timeline (optional)

- **Import Roster** (Characters tab): paste the JSON response from HoYoLAB's `api/character/list` endpoint (via browser DevTools → Network tab) to sync ownership and constellations.
- **Import GOOD Data** (Weapons tab): paste a [GOOD-format](https://frzyc.github.io/genshin-optimizer/#/doc) JSON export to sync weapon refinements and character constellations at once.
- **Import Calendar** (Timeline tab): paste the JSON response from HoYoLAB's `act_calendar` endpoint to populate the banner/event Gantt chart.

## Project structure

```
.
├── wish-counter.html   # Page markup only
├── styles.css          # All styling
├── script.js           # All application logic (state, rendering, imports)
└── README.md
```

The three files must stay in the same directory — `wish-counter.html` references the other two via relative `<link>`/`<script src>` paths.

## Data & privacy

- All wish, roster, timeline, and settings data lives in your browser's `localStorage` under the `wishCounter.*` keys. Clearing your browser data will erase it — use **Settings → Export backup** periodically to save a JSON copy you can restore later.
- The app fetches directly from HoYoverse's public wish-history API (with a couple of CORS-relay fallbacks if a direct request is blocked) and, optionally, from HoYoLAB for roster/timeline imports. No wish or account data is sent anywhere else.
- Character/weapon portrait art is hotlinked from [paimon.moe](https://paimon.moe); weapon type icons are hotlinked from the [Genshin Optimizer](https://github.com/frzyc/genshin-optimizer) asset CDN.

## Deploying your own copy with GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch," pick your default branch and the `/ (root)` folder.
4. Save. Your site will be published at `https://<username>.github.io/<repo>/wish-counter.html`.

## Acknowledgements

- Wish-history API access pattern based on the community-standard [GachaLogQuery](https://gist.github.com/MadeBaruna/1d75c1d37d19eca71591ec8a31178235) PowerShell script.
- Timeline/Gantt-chart concept inspired by [paimon.moe](https://paimon.moe).
- Icons from [Lucide](https://lucide.dev) (ISC licensed).

## License

MIT — see [LICENSE](LICENSE) for details.

## Disclaimer

Wish Counter is an unofficial, fan-made tool and is not affiliated with, endorsed by, or connected to HoYoverse/miHoYo. Genshin Impact and all related assets are trademarks of HoYoverse.
