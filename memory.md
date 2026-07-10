# memory.md — matchavez/hockeyrosters

Self-context for Claude. No README.md currently exists in this repo (single `index.html` file) — note this rather than assume; if a human-readable README gets added later, keep it and this file in sync per the standing instruction. Last refreshed: 2026-07-11.

## What this repo is
Single-page site at `https://matchavez.com/hockeyrosters` — talent-facing roster-PDF downloads for NZIHL/NZWIHL broadcast booth. GitHub Pages, one `index.html`, no build step.

## What it does
- Renders matchup cards for upcoming games, each linking to that game's roster PDF (sourced from the `nzihl-broadcast-rosters` / `nzwihl-broadcast-rosters` repos' release artifacts / `boxscores.json` manifest).
- Manifest-driven "Coming soon" state for games whose PDF isn't posted yet.
- Weekend series (same matchup, legs ≤3 days apart) combine into a single card; on narrow layouts (<~500px) the two legs stack instead of sitting side by side; cards are capped at ~500px so two fit side by side in the grid.
- Uses team short codes (see nzihl-broadcast-rosters' `teams.py` registry for the canonical codes — note ADM replaced the legacy WAA code for Pure NZ Admirals as of 2026-07-10).
- Lookahead window for what's shown was widened to 11 days (2026-07-05); this is independent of the 4-day PDF-generation window used by the roster-builder repos.
- Past games with no PDF ever posted get dropped from the latest release view rather than showing a stale "coming soon" card (fixed 2026-07-07).

## Recent history worth knowing (most recent first)
- 2026-07-08: series card sizing/stacking polish (cap ~500px, stack under ~500px).
- 2026-07-07: drop past games with no PDF from latest release.
- 2026-07-04: copy updated for the 11-day upcoming-games window.
- 2026-07-02: per-league "quiet week" card copy, clarified "rosters include prior-game stats, post by 7am on game day" messaging.

## Related repos
- **matchavez/nzihl-broadcast-rosters**, **matchavez/nzwihl-broadcast-rosters** — actually generate the roster PDFs (daily cron 17:30 UTC) and the `boxscores.json` gameid manifest this page reads to know what's playable/postable.
- **matchavez/hockey** — the broader portal; links to this page.

## Sync note
Keep this file (and README.md, if one gets added) in sync with every meaningful change. If they drift, flag it to Mat and get approval before publishing the sync rather than doing it silently.
