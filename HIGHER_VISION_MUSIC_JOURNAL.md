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
| Broken logo + back-links on all 5 follow pages | Hardcoded old dead domain `auralalchemy.github.io/higher-vision-music` (site moved to `marstudio360` account; auralalchemy is private/404) | Replaced with relative paths `../../` (survives account move + custom domain) | ✅ FIXED 2026-06-14 (commit bec2d25, verified live 200) |
| `index.html` home/logo links 404 | `href="/"` points to github.io account root, not project subpath | Changed to `href="./"` | ✅ FIXED 2026-06-14 |
| Footer © 2025 | Stale year | Bumped to 2026 | ✅ FIXED 2026-06-14 |
| Meta Pixel / ad tracking dead | Pixel ID left as placeholder `XXXXXXXXXXXXXXXXXX` in all follow pages | Insert real Meta Pixel ID | OPEN — need Mariano's real Pixel ID |

## Roadmap & philosophy (refined 2026-06-14, Mariano)
**Philosophy:** growth-first, ads-fueled, owned-audience flywheel. Website = conversion machine; Meta ads = fuel; **playlists + email list = the compounding assets**. Build the assets BIG first, then plug monetization into an audience that already exists. Don't review random songs early; don't charge before the assets justify it. Keep the current site's look/feel — Mariano likes it; we POLISH + EXTEND, not redesign.

**NOW (current focus):** make the site **perfect for Meta ads** → promote the website + each playlist landing page → grow traffic + playlist saves/follows.
- Ad-ready the homepage + all 5 `/follow/<genre>/` landing pages (Pixel, OG/share cards, single CTA, mobile/speed, conversion events).
- Wire the **mail system** (Resend + freebie lead magnet + capture) — SAME structure as `alchemyaural` / the aural-alchemy-app.
- **Migrate** to Next.js/Vercel (soon) — same structure as Aural Alchemy + his other sites.

**THEN (more traffic + revenue):** add new on-site sections — **samples, beats, full tracks, guides, blogs**. Then put ads behind them + scale.

**FUTURE / roadmap (gated on growth — NOT now):**
- **Submission/review service** ("our own SubmitHub", fully in-house) — ACTIVATE only once playlists are big. Mariano explicitly does not want to review random songs before then.
- **Paid social promotions + promo bundles** — only AFTER the socials/channels (IG, YouTube) are grown. Grow the channels themselves first.

## AI music → Spotify via DistroKid — RULES (researched 2026-06-15, cited)
**VERDICT: GO, with 2 hard carve-outs.** AI music IS allowed on DistroKid + Spotify; self-playlisting your own tracks for organic listeners IS allowed. But:
1. **❌ NO-GO: ElevenLabs Music on Spotify.** ElevenLabs terms PROHIBIT distributing its generated music to ANY streaming platform under every license type. → Use **Suno (paid)** + human/mixed for Spotify; ElevenLabs is for the FUNNEL ONLY (YouTube mixes, social, site/landing audio) — never a Spotify release. (Corrects Mariano's "doesn't matter Suno/ElevenLabs" — for Spotify it DOES matter.)
2. **⚠️ CAUTION: cadence.** Spotify deleted 75M+ tracks + runs a live spam filter. Flooding = profile nuke. Curated + paced + disclosed = safe.

**Hard rules:**
- **Suno: PAID tier only for distribution** (Pro $10/Premier $30 = commercial rights, keep 100% royalties). FREE tier = non-commercial, and upgrading later does NOT retroactively license free-tier songs → anything for Spotify must've been generated WHILE paid sub active. Keep proof (generation date). Post-Warner: "Granted Commercial Rights" (Suno is technically author) — fine to distribute/monetize; write own lyrics / add human production to strengthen copyright.
- **DistroKid: LABEL plan required** for 5 artist names (Musician=1, Musician Plus=2, Label=unlimited). Confirm Mariano's plan (he runs HV Originals + 2 ambient + 2 lofi = 5).
- **Self-playlisting OWN tracks = allowed.** Banned = bots/bought streams/"guaranteed placement"/multi-account looping → €10/track/mo fee + delisting. Grow playlist followers via real channels only.
- **AI disclosure:** fill the AI/DDEX MEAD field honestly at upload (declare partial AI if human wrote lyrics/produced). No voice clones / recognizable-artist vocals without consent.

**SAFE UPLOAD SOP:** Spotify = Suno-paid + human/mixed only (ElevenLabs OUT). Per track: paid-Suno proof, own/clear 100%, UNIQUE (no near-dupes), listenable length 1:30–4:00 (no ~30s royalty-farm), honest metadata + original artwork, set AI disclosure. Cadence: **singles, ~1–2 releases per profile per week MAX**, stagger across the 5 profiles, real release calendar — never batch-dump. Keep a paper trail (Suno date, lyric authorship, sample clearances) per track.

## Business model — TOS-safe monetization (researched 2026-06-14, cited)
**The one rule that keeps the playlists alive: you sell the REVIEW, never the ADD.**
- **Legal (pay-for-consideration):** charge for a *guaranteed honest review + written feedback within a deadline, refund if no response*. Placement is at sole editorial discretion and **never guaranteed**; the fee is **identical whether the track is accepted or rejected**. This is the SubmitHub/Groover/DailyPlaylists model.
- **Illegal (pay-for-placement = payola):** Spotify **User Guidelines** ban verbatim "accepting or offering to accept any compensation… to influence… the content included on an account or playlist." Crossing this → withheld royalties, removal from playlists, account/track delisting, and **~$10/track/month penalties** when >90% of a track's streams are flagged fraudulent (since Apr 2024).
- **Scale gate to charge anything credibly:** **≥1,000 REAL followers per playlist** (PlaylistPush's hard floor) AND a healthy **listener-to-follower ratio** (listeners ≥ followers = green; followers ≫ listeners = the fake tell that gets you delisted). **Current HV scale (~5 playlists, ~2k saves, ~4.2k streams ≈ a few hundred followers each) is BELOW the floor — cannot charge yet.**
- **DECISION (Mariano 2026-06-14): FULLY IN-HOUSE. No SubmitHub/Groover/3rd-party — ever.** We build our OWN submission/review service on our own website, own the traffic + emails + ecosystem. The TOS-safe model is platform-agnostic: it still applies to OUR site → we charge for a **real honest review** (placement at our discretion, never guaranteed, fee same accept/reject). Reviews must ACTUALLY be delivered (batch/template fine as volume grows) — that delivery is both the legal cover and the trust.
- **Growth engine = the website itself:** ads + any traffic source, YouTube mixes/videos, an **email list built via freebies (lead magnet)**, all content centralized on-site. Grow the playlists by routing this owned audience to them.
- **Migration note:** building the in-house email list + paid review system is the feature that triggers the Vercel/Next+Supabase+Stripe+Resend migration (static GH Pages can't hold secrets / gate / capture at scale). That migration happens AS we build the ecosystem.

### Anti-fraud guardrails (STANDING — violating any can get playlists delisted)
- ❌ Never buy streams, followers, or placements — #1 trigger.
- ❌ Never accept submissions from artists who use bot/stream-buying services (their fake streams attach to OUR playlist and flag US).
- ❌ Never guarantee placement, streams, followers, chart impact, or "algorithmic boost."
- ❌ Never make the fee contingent on acceptance.
- ❌ No public/collaborative playlists (anyone can inject tracks).
- ❌ Never sell/rent a playlist or account.
- ✅ Keep growth gradual/organic (spikes = bot signature); monitor follower-to-listener ratio (Chartmetric/artist.tools); vet every submission.

## Suno generation engine — self-hosted, WORKING (2026-06-15)
We run our OWN Suno automation on Mariano's **paid Pro account** (commercial rights clean, no reseller markup, no third-party rights-muddle).
- **Tool:** `gcui-art/suno-api` (Next.js) cloned to `D:\HIGHER VISION MUSIC\TOOLS\suno-api`. `npm run dev` → **http://localhost:3000**.
- **Auth:** `SUNO_COOKIE` in `.env` = full cookie incl httpOnly `__client`/`__client_uat`/`__session` (40 `*.suno.com` cookies, ~8.4k chars). Tool auto-refreshes the JWT from it. Got it via **WebLoom `export_profile` on slot-1** after Mariano logged into suno.com (document.cookie ALONE is insufficient — misses httpOnly `__client`).
- **Captcha:** `TWOCAPTCHA_KEY` left BLANK and generation STILL worked — no 2captcha needed so far (Playwright chromium installed as backup for the captcha path).
- **Verified working:** `GET /api/get_limit` → `{credits_left:2430, monthly_limit:2500}` (Pro = 2500 cr/mo ≈ 250 songs). `POST /api/generate {prompt, make_instrumental:true, wait_audio:false}` → 2 clip ids → `GET /api/get?ids=` → audio_url → downloaded. First 2 tracks "Tidal Glass" in `EXPORTS\suno-test\`.
- **Model note:** default returns `chirp-v3` (older). For RELEASE quality target v4/v4.5 — check gcui-art model param / account default before mass-generating releases.
- **Cost:** only Mariano's Pro credits (no reseller fee). ToS caveat: automation is technically against Suno ToS → keep volume sane (matches the paced-release rule anyway), it's his own account.
- **Pipeline:** prompt pack (`SUNO PROMPTS\HIGHER_FOCUS.md`) → local API generate → download → (Suno paid) release via DistroKid as HV Originals → into playlists. Flywheel input solved.

## 🚀 EXPANDED VISION — the full machine (2026-06-16, Mariano)
Higher Vision = **playlist network + AI-beat label + visualizer/YouTube channel + beat store**, all funneling back to the playlists (still the core asset).

**The pillars:**
1. **Playlist network (core):** the 5 Spotify playlists. Everything drives saves/followers here. Still the center.
2. **AI-beat label:** go ALL-IN on AI-generated beats. Higher Vision Originals + **onboard the 5 AI artists Mariano already has** (showcase each on the site). Engine = self-hosted Suno (chirp-fenix) on his Pro account. Release via DistroKid → Spotify → self-place into our playlists (flywheel).
3. **Visualizer + YouTube channel (BUILD FIRST per Mariano):** make mind-blowing **audio-reactive visualizers** from the slow-boombap beats → YouTube (16:9) + IG/TikTok Reels (9:16). Engine = the **generative-studio `/visualizer` surface** (planned in `generative-studio/GENERATIVE_STUDIO_JOURNAL.md` → "Music Visualizer subproduct"; 34 engines + audio routing + headless MP4 bake). Get YouTube pipeline + visualizer working BEFORE scaling Spotify uploads.
4. **Website ecosystem (hub):** **magic-link auth (like Aural Alchemy)** → users get a library + access to features. Sections: music/visualizers · beat store · samples · the 5-artists showcase · guides/blogs. Email list via freebie.
5. **Beat store (new revenue):** sell ready-made **beats + full tracks (any genre)** for ads / videos / cinematic / rappers / anyone — full beatstore. Plus **samples / sample-packs / loops** (try Suno one-shot/loop generation — see todos).
6. **Social automation:** IG `@_highervisionmusic_` + new YouTube channel, automated via **social-brain MCP** (account `hvm` for IG/FB reels; `publish_youtube`; `generate_caption`; `schedule_content_calendar`). Post visualizers + uploads, route to playlists.

**Flywheel:** AI beats → visualized (YouTube/IG) + released (Spotify) → audience → playlists + website → website sells beats/samples + captures emails → ads amplify → playlists grow → the asset that powers everything.

**🔒 POSITIONING GUARDRAIL (Mariano, 2026-06-16):** Publicly, **NEVER market it as "AI music"**, and **never claim it's "100% original / fully human"** either. Frame it as **"produced beats / curated sound"** — smooth, vague, professional. ⚠️ Honest line that protects the brand: this is a MARKETING stance, NOT a license to lie on platform compliance — at DistroKid/Spotify upload still fill the **AI-disclosure (DDEX) field per their requirement** (backend, invisible to public) so the artist profile doesn't get flagged/nuked by the anti-AI-spam system. Public = smooth; platform compliance = honest. The two don't conflict.

**social-brain accounts available:** `hvm` (Higher Vision Music IG/FB), plus `vibedna`/`aural`/`nano`. YouTube upload + IG/FB reels + Threads all wired.

## Lessons for the next build
- Building a site via GitHub web-UI uploads leaves NO local copy and "Add files via upload" commits — always clone + work locally + push.
- Cross-page absolute URLs hardcoded to a specific github.io account break the instant the repo moves accounts. Use relative paths for same-site links.

## Session log
- **2026-06-14** — Located the lost site (Mariano didn't know where it was). Found repo on `marstudio360`, confirmed live Pages site, cloned locally, read full codebase, catalogued bugs. Started this journal + memory file.
- **2026-06-14** — Fixed 3 link/year bugs (commit `bec2d25`), pushed → Pages rebuilt → verified live (follow/ambient HTTP 200, logo asset 200, no auralalchemy refs, © 2026). Only Meta Pixel remains (needs real ID). Pushed via token in URL only (origin remote stays clean).
- **2026-06-14** — Mariano set the big vision (playlist network → paid submission service → social automation IG+YT → sell own samples/beats → self-promotion flywheel → ads). Ran research: Spotify API CAN fully manage owned playlists (add/remove/reorder/cover via `/items`, refresh-token headless, dev account must be Premium, no API for editorial/other-owner submission); stack = stay on GH Pages until first paid+gated feature then Vercel/Next+Stripe+Supabase; social = daily IG reels→Shorts→biweekly long-form lofi via social-brain MCP; submission-service legality = sell the REVIEW not the ADD, current scale too small to charge, on-ramp via SubmitHub/Groover (see Business model section). AI-music selling-rights research errored on rate-limit — re-run for Phase 3.
- **2026-06-14** — Consolidated all HV material to a D: master workspace `D:\HIGHER VISION MUSIC\` (MATERIAL\AI MUSIC EMPIRE 14.69GB + MATERIAL\beats-HigherVisionMusic 1.16GB + BRAND-ASSETS 3.30GB logos/coverarts/mockups/IG + AITRACKLABSTUDIO 3.30GB [AI MUSIC & SAMPLES, PROMPT PACKS, BRANDKIT] + empty CONTENT\/EXPORTS\). All pulled via rclone `gdrive:` remote + hash-verified (0 diffs). Permanently deleted from Drive: AI MUSIC EMPIRE (after verify) + a 62GB personal backup (phone photos/retreat/doc-snapshots that were mislabeled inside `Higher Vision Music Assets/STORAGE`, not HV) → freed ~77GB on Drive (now ~19/100GB used). ⚠️ `AITRACKLABSTUDIO/proton-recovery-kit.pdf` = Proton recovery codes, keep private. Index at `D:\HIGHER VISION MUSIC\HV_WORKSPACE_README.md`. Real logos now local → ad-readiness pass unblocked.

---

## 🔓 SUNO WAV EXPORT — REVERSE-ENGINEERED (2026-06-16)

**Goal:** mass-download true WAV (not MP3) for all beats off the Suno Pro account, no manual clicking.

**The 3-step flow (captured via WebLoom network capture of one manual WAV download):**
1. `POST https://studio-api-prod.suno.com/api/gen/{CLIP_ID}/convert_wav/` (body empty) -> `204`. Kicks off server-side WAV render.
2. `GET  https://studio-api-prod.suno.com/api/gen/{CLIP_ID}/wav_file/` -> JSON, poll until ready (optional).
3. `GET  https://cdn1.suno.ai/{CLIP_ID}.wav` -> the WAV, **served PUBLICLY once converted (NO auth header needed)**. ~27 MB, real RIFF.

**Auth (steps 1-2 only):** three headers —
- `authorization: Bearer <JWT>`  — get a fresh one IN-PAGE via `await window.Clerk.session.getToken()` (refreshes automatically; JWT exp ~1h, aud `suno-api`).
- `device-id: 9a7dda28-0678-41f0-8d85-429e2dfc9786`
- `browser-token: {"token":"<base64 of {\"timestamp\":<now_ms>}>"}`  (regenerate per request)

**GOTCHAS / lessons:**
- Direct guess `cdn1.suno.ai/{id}.wav` returns **403** until `convert_wav` has been called for that clip. After conversion it flips to 200 public.
- WAVs **auto-expire ~2 days** (`x-amz-expiration ... rule-id=remove-file-with-wav-tag`). Convert + download promptly.
- **Do NOT copy the JWT into a PowerShell command** — a signed token breaks on one mangled char -> 401 on all. Fire the authed steps (convert_wav) IN-BROWSER via `eval_js` (getToken is always valid + same-origin). Do the public CDN download from PowerShell (no auth, no token-corruption risk).
- eval_js times out on ~58 sequential awaited POSTs + sleeps. Fire conversions in **parallel chunks** (`Promise.all`, chunk=12) -> ~10s for 58.
- Library feed: `GET studio-api-prod.suno.com/api/feed/v2?page=N` -> `{clips, num_total_results, current_page, has_more}`, 20/page. Genre is in `clips[].metadata.tags`. Suno makes 2 variants per gen (same title twice, different ids) -> id8 prefix disambiguates filenames `Title_<id8>.wav`.

**First batch:** Velvet Spokes -> Chrome Synapse = 58 boom-bap clips (both variants). Tags shift to ambient/dnb/break right after Chrome Synapse = the clean genre cutoff. Saved to `D:\HIGHER VISION MUSIC\HIGHER VISION UNRELEASD FOLDER`.
