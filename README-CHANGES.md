# ICED By Becky — Gallery Expansion (v3, commit-ready)

Copy the contents of this folder over the repo root, preserving paths, then commit.
Supersedes v1 and v2.

## IMPORTANT: css/style.css is NOT part of this package
Do not copy any stylesheet. The filter styling now lives in a <style> block inside each
gallery page, and filtering itself no longer depends on any stylesheet at all. If you
already committed the v2 css/style.css, that is harmless — its extra rules are simply
unused — but you can also revert it.

## Why v2 failed on the live site
Two separate defects, both now fixed:

1. Filtered-out images stayed visible. The code hid them with an `.is-hidden` class defined
   in css/style.css. The live site was still serving the previous stylesheet, so the class
   matched no rule and nothing hid — the count read "Showing 2 of 36" while all 36 rendered.
   Fix: the JS now writes `style.display` directly on each image. An inline style outranks
   every stylesheet rule, so filtering works even if a stylesheet is stale, cached, or never
   redeployed.

2. The "Clear filters" button never appeared. It shipped with the `hidden` attribute and the
   JS only toggled `style.display`, so the attribute kept it hidden. Fix: both the attribute
   and the inline style are now managed together.

Related background: css/style.css line 42 declares `img { max-width: 100%; display: block; }`.
An author rule like that overrides the browser default of `[hidden] { display: none }`, which
is why the `hidden` attribute alone can never hide a gallery image on this site.

## Files changed (4)
- `cookie-gallery.html`  — dropdown filters + 36 tagged images (was 15)
- `cupcake-gallery.html` — dropdown filters + 9 tagged images (was 8)
- `cakepop-gallery.html` — dropdown filters + 4 tagged images
- `pricing.html`         — "See examples" tier links on all three price cards

## Files added (22)
All in `images/` — renamed and resized to 1600px max width to match site convention.

## Verified in Chromium against the ORIGINAL, UNMODIFIED css/style.css
Every assertion is on real rendered geometry and computed display, never on the properties
the code sets. In every case the stated count equals the number of images actually rendering.
Covered: default load, each tier, each occasion, combined axes, empty combinations, the
empty-state message, Clear filters appearing and clearing, deep links preselecting both
dropdowns, invalid URL params, all three galleries, pricing links, and 390px mobile. No JS
errors, no broken images.
