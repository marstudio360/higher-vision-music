# Higher Vision Music — Engineering Journal

Curated Spotify playlist network / "record label" landing site.
Tagline: **"Music Without Limits. Every Genre. One Vision."**

## Where it lives
| Thing | Value |
|---|---|
| GitHub repo | https://github.com/marstudio360/higher-vision-music (public, `marstudio360` account) |
| Live site | https://marstudio360.github.io/higher-vision-music/ (GitHub Pages, main/root) |
| Local clone | `C:\Users\Pierina Marchesoni\Desktop\NANO VIBE CODING\HIGHER VISION MUSIC` |
| Stack | static HTML/CSS/JS — no framework, no build. `git push` → Pages auto-deploys |
| Auth | `marstudio360` GitHub token in vault entry `github` (access_token) |

## Structure
- `index.html` — home: nav, hero (+ animated genre ticker), stats (5 / 2,000+ saves / 4.2K streams), filterable 5-playlist grid (Spotify embeds), follow CTA, footer
- `style.css`, `script.js` — shared home assets (nav toggle, reveal-on-scroll, filter pills, live stream count)
- `HigherVision_Logo_White_NoBG.png` — logo
- `follow/{ambient,bass,chillhop,focus,lofi}/index.html` — per-playlist follow-gate landing pages. Self-contained (inline CSS), Meta Pixel + `trackFollow()` firing `Lead` + custom `SpotifyFollow` on CTA click. Built for paid traffic.

## Playlists (Spotify IDs)
| Name | Genre | Playlist ID |
|---|---|---|
| Higher Chillhop | Chillhop/Jazz | `0wnaqMsSPArsxXk1h42DyM` |
| Higher Ambient | Ambient/Atmospheric | `4eAlW29otq3YHe5SSlSEF5` |
| Higher Lofi | Lofi/Beats | `5eS8QxWKaRxC3HfMIaMALK` |
| Higher Focus | Focus/Deep Work | `2NF0pR8dLlmq0YKxN2cVMr` |
| Higher Bass | Bass/Electronic | `14RfqVAJRW1vaGnvI6O9Uv` |

Spotify profile: `open.spotify.com/user/12181937778` · IG `@_highervisionmusic_` · FB `highervisionmusic`

## Bug → Root Cause → Fix
| Bug | Root cause | Fix | Status |
|---|---|---|---|
| Broken logo + back-links on all 5 follow pages | Hardcoded old dead domain `auralalchemy.github.io/higher-vision-music` (site moved to `marstudio360` account; auralalchemy is private/404) | Replace with `marstudio360.github.io/...` or relative paths | OPEN |
| Meta Pixel / ad tracking dead | Pixel ID left as placeholder `XXXXXXXXXXXXXXXXXX` in all follow pages | Insert real Meta Pixel ID | OPEN |
| Footer © 2025 | Stale year | Bump to 2026 | OPEN |

## Lessons for the next build
- Building a site via GitHub web-UI uploads leaves NO local copy and "Add files via upload" commits — always clone + work locally + push.
- Cross-page absolute URLs hardcoded to a specific github.io account break the instant the repo moves accounts. Use relative paths for same-site links.

## Session log
- **2026-06-14** — Located the lost site (Mariano didn't know where it was). Found repo on `marstudio360`, confirmed live Pages site, cloned locally, read full codebase, catalogued 3 open bugs above. Started this journal + memory file.
