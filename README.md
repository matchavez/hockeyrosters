# hockeyrosters

Game-day roster PDF downloads for NZIHL & NZWIHL broadcast talent.

Live at **https://matchavez.com/hockeyrosters** (GitHub Pages, deploy = push to `main`). Single-file `index.html`, no build step.

## What it does

Lists upcoming NZIHL/NZWIHL games as matchup cards, each linking to that game's downloadable roster PDF. Cards read a manifest (`boxscores.json`, published by the roster-builder repos) to know which games are coming up and which already have a PDF posted.

- **Weekend series** (same matchup, legs ≤3 days apart) combine into a single card — side by side above ~500px wide, stacked below it.
- **"Coming soon"** cards show for games in the manifest that don't have a PDF yet (rosters are typically posted by 7am on game day, and include stats through the prior game).
- Past games that never got a PDF drop out of the latest view instead of showing a stale "coming soon" card.
- The page looks ahead **11 days**; the roster PDFs themselves are only generated 4 days out, so the last several days of that window will legitimately show "coming soon" until closer to the date.
- Per-league "quiet week" messaging when one league has no games in the window, rather than just omitting the section.

## Where the data comes from

- **matchavez/nzihl-broadcast-rosters** and **matchavez/nzwihl-broadcast-rosters** generate the actual roster PDFs (daily GitHub Actions run, ~17:30 UTC) and publish `boxscores.json`, which this page fetches to build its manifest.
- Team short codes match the Style Guide TLAs (e.g. `ADM` for Pure NZ Admirals) used across the roster/standings repos.

## Related

- **matchavez/hockey** — the broader NZIHL/NZWIHL broadcast portal, links to this page.
