# ICED By Becky — icedbybecky.com

Static website for ICED By Becky, deployed on GitHub Pages with a custom domain.

## Deploy to GitHub Pages (one-time setup)

1. Create a new GitHub repository (e.g. `icedbybecky`), public.
2. Upload the entire contents of this folder to the repo root (or `git init`, commit, push).
3. Repo → Settings → Pages → Source: **Deploy from a branch** → Branch: `main` / root → Save.
4. Settings → Pages → **Custom domain**: enter `icedbybecky.com` → Save.
   (The `CNAME` file in this folder does the same thing — keep it in the repo.)
5. Check **Enforce HTTPS** once the certificate provisions (can take up to an hour).

## GoDaddy DNS (delete the old forwarding first!)

Domain → DNS → Manage records:
1. **Delete** any Forwarding / masking rules.
2. Add four **A records**, name `@`, pointing to GitHub Pages:
   - 185.199.108.153
   - 185.199.109.153
   - 185.199.110.153
   - 185.199.111.153
3. Add a **CNAME record**: name `www` → value `<your-github-username>.github.io`
4. Wait for propagation (minutes to a few hours), then verify in repo Settings → Pages.

## Editing content

- Pages are plain HTML: `index.html`, `gallery.html`, `cookie-gallery.html`,
  `cupcake-gallery.html`, `pricing.html`, `faq-about.html`, `contact.html`.
- All styling lives in `css/style.css`. Brand colors are CSS variables at the top.
- **Update the Shop URL**: search all files for `icedbybecky.square.site` and replace
  with the actual Square site URL if different.

## Adding gallery photos

1. Drop the photo into `images/` (JPG, ~1200–1600px wide is plenty; compress first).
2. In `cookie-gallery.html` or `cupcake-gallery.html`, duplicate one line inside
   `<div class="gallery-grid">`:

   ```html
   <img src="images/YOUR-PHOTO.jpg" alt="Describe the cookie set" loading="lazy">
   ```

That's it — commit/upload and GitHub Pages redeploys automatically.
