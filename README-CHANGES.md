# ICED By Becky — Gallery Expansion (commit-ready)

Copy the contents of this folder over the repo root, preserving paths, then commit.

## Files changed (4)
- `cookie-gallery.html`  — filter bar + 36 tagged images (was 15)
- `cupcake-gallery.html` — filter bar + 9 tagged images (was 8)
- `cakepop-gallery.html` — filter bar + 4 tagged images (unchanged count, now tagged)
- `pricing.html`         — "See examples" tier links added to all three price cards
- `css/style.css`        — appended `.gallery-filters` block at end; nothing above it touched

## Files added (22)
All in `images/` — renamed and resized to 1600px max width to match existing site convention.

## How it works
Each `<img>` carries `data-occasion` and `data-tier`. A small inline vanilla-JS block at the
bottom of each gallery page filters on both axes (AND), mirrors state to the URL
(`?occasion=birthdays&tier=elaborate`), and shows a friendly message when a combination is
empty. Tier is never displayed on an image — it exists only as a filter and a link target.
No build step, no dependencies, no changes to header/footer/nav.

## Verified
- All 49 image references resolve
- Filter combinations, deep links, URL sync, reset, and invalid params tested in Chromium
- Desktop and mobile (390px) layouts checked
