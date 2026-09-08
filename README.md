# REEF OXP Booking System — Staff Guide (Dashboard)

A single navigable dashboard combining the 8 staff pilot handoff documents
into one site with a persistent sidebar. Each original guide is untouched
in `guides/` — `index.html` is a thin shell that loads them into an iframe
and keeps the sidebar highlighted/synced via the URL hash (e.g.
`index.html#status-guide` links straight to the 8-Stage Status Guide).

## Structure
- `index.html` — the dashboard shell (nav + iframe). No build step.
- `guides/01-quick-guide.html` — Staff Quick Guide (originally Sept 3, 2026)
- `guides/02-demo-story.html` — Demo Story & Click-Through (originally Sept 3, 2026)
- `guides/03-source-of-truth.html` — Source-of-Truth Map (Sept 8, 2026)
- `guides/04-status-guide.html` — 8-Stage Bookings Status Guide (Sept 8, 2026)
- `guides/05-manual-fallback.html` — Manual Fallback Guide (Sept 8, 2026)
- `guides/06-testing-instructions.html` — Staff Testing Instructions (Sept 8, 2026)
- `guides/07-bug-reporting.html` — Bug-Reporting Process (Sept 8, 2026)
- `guides/08-first-booking.html` — First Real Booking Checklist (Sept 8, 2026)

## Updating a guide
Edit the relevant file in `guides/` directly (same HTML/CSS structure as
before — nothing about combining them into the dashboard changed how each
page is authored). The dashboard shell (`index.html`) never needs to
change unless a page is added, removed, or renamed.

## Adding a new guide
1. Drop the new HTML file into `guides/`.
2. In `index.html`, add one entry to the `PAGES` object (key → file path).
3. Add a matching `<a class="navlink" data-key="...">` in the sidebar markup.

## Hosting
Static site, no build step — works from GitHub Pages (Settings → Pages →
Deploy from branch → `main` → `/root`), or any static host, or by opening
`index.html` directly from disk.
