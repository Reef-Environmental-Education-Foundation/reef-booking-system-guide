# REEF Staff Systems Guide (Dashboard)

This is the **live, canonical** staff guide site covering REEF's front-line Airtable-interface
workflows: the **REEF Booking System** (**Ocean Explorers/OXP** + **Facility Rentals**) and,
as of 2026-09-10, **Free Event Check-In** (the EPO base). OXP was built out first, so the booking
side of the content is OXP-only for now; Facility Rentals content will be added as a second
booking section once it exists. The repo/URL slug (`reef-booking-system-guide`) predates the
Check-In section and stays as-is so existing bookmarks keep working — the on-page title and nav
now read "REEF Staff Systems Guide" to reflect the broader scope. Worth revisiting the slug itself
if more non-booking sections get added later.

A single navigable dashboard combining the staff pilot handoff documents into one site with a
persistent sidebar. `index.html` is a thin shell that loads each guide into an iframe and keeps
the sidebar highlighted/synced via the URL hash (e.g. `index.html#status-guide` links straight to
the 8-Stage Status Guide) — so any section can be linked to directly.

**This repo is the source of truth.** A copy also exists in Martha's Dropbox for internal
reference only (not staff-facing) — it is archived and not kept in sync. Any update to the guide
should be made here, on `main`, not in Dropbox.

## Structure
- `index.html` — the dashboard shell (nav + iframe). No build step.
- `01-quick-guide.html` — Staff Quick Guide (Ocean Explorers/OXP)
- `02-demo-story.html` — Demo Story & Click-Through (OXP)
- `03-source-of-truth.html` — Source-of-Truth Map (OXP)
- `04-status-guide.html` — 8-Stage Bookings Status Guide (OXP)
- `05-manual-fallback.html` — Manual Fallback Guide (OXP)
- `06-testing-instructions.html` — Staff Testing Instructions (OXP)
- `07-bug-reporting.html` — Bug-Reporting Process (OXP)
- `08-first-booking.html` — First Real Booking Checklist (OXP)
- `09-checkin-guide.html` — Event Check-In Staff Guide (EPO base). Two tabs: Any event, and REEF Fest. Covers the Event Check-In interface (Start Here, Step 2, Step 3), the contact notice and opt-out step. Replaces the earlier guide for the Admin Event Check-In interface, which is kept in git history.

Files are flat at the repo root (not nested in a `guides/` folder) because GitHub's web upload
flow doesn't preserve subfolders when files are added individually.

## Updating a guide
Edit the relevant file directly and commit to `main` — GitHub Pages redeploys automatically
within seconds. The dashboard shell (`index.html`) never needs to change unless a page is added,
removed, or renamed.

## Adding a new guide (e.g. the future Facility Rentals section)
1. Add the new HTML file at the repo root.
2. In `index.html`, add one entry to the `PAGES` object (key → file path).
3. Add a matching `<a class="navlink" data-key="...">` under the right `program-heading` group in
   the sidebar markup (there's already a placeholder "Facility Rentals" heading with a disabled
   "Guide coming soon" row — replace that row with real links once content exists).

## Hosting
Static site, no build step — GitHub Pages, Settings → Pages → Deploy from branch → `main` →
`/(root)`. Live at: https://reef-environmental-education-foundation.github.io/reef-booking-system-guide/
