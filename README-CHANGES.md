# ICED By Becky — Gallery Expansion (v2, commit-ready)

Copy the contents of this folder over the repo root, preserving paths, then commit.
This supersedes the earlier package.

## Changes from v1
- Filters are now **dropdown menus** (one selection per axis) instead of button pills.
- **Bug fix:** filtered-out images stayed visible. `css/style.css` line 42 sets
  `img { max-width: 100%; display: block; }`, and an author rule like that overrides the
  browser's built-in `[hidden] { display: none }`. Hiding now uses an `.is-hidden` class
  with a rule specific enough to win; the `hidden` attribute is still set for screen readers.
- Dropdown options show a count per value, e.g. "Birthdays (16)".
- Added a "Clear filters" button that appears only while a filter is active.

## Files changed (5)
- `cookie-gallery.html`  — dropdown filters + 36 tagged images (was 15)
- `cupcake-gallery.html` — dropdown filters + 9 tagged images (was 8)
- `cakepop-gallery.html` — dropdown filters + 4 tagged images
- `pricing.html`         — "See examples" tier links on all three price cards
- `css/style.css`        — appended `.gallery-filters` block at end; nothing above it touched

## Files added (22)
All in `images/` — renamed and resized to 1600px max width to match site convention.

## Verified in Chromium
Filtering asserted against real rendered geometry (bounding box + computed display), not the
`hidden` property — that circular check is what let the v1 bug through. Covered: default load,
each tier, combined axes, empty combinations, Clear filters, deep links preselecting the
dropdowns, invalid URL params, and desktop + 390px mobile layouts. No JS errors.
