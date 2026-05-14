# Basilisk Systems — Netlify-ready Hugo update

This update contains the modern custom CSS Basilisk design plus Netlify deployment fixes.

## What is included

```text
layouts/_default/basilisk.html
content/en/index.md
content/pl/index.md
content/fr/index.md
static/img/baz.jpg
static/img/baz_li.png
static/img/logo_b.png
static/img/logo_w.png
static/_redirects
hugo.toml
netlify.toml
```

## Why this fixes Netlify 404

Netlify must publish Hugo's generated `public/` folder, not the repository root. The included `netlify.toml` sets:

```toml
[build]
  command = "hugo --minify"
  publish = "public"
```

The multilingual homepage lives at `/en/`, `/pl/`, and `/fr/`. The root URL `/` redirects to `/en/`.

## Apply from the project root

```bash
unzip basilisk_netlify_update.zip
cp -r basilisk_netlify_update/* .
rm -rf public resources
hugo server -D --disableFastRender
```

Open locally:

```text
http://localhost:1313/en/
http://localhost:1313/pl/
http://localhost:1313/fr/
http://localhost:1313/img/baz.jpg
```

## Deploy to Netlify

```bash
git add .
git commit -m "Add Netlify-ready Basilisk Hugo site"
git push
```

Then in Netlify:

```text
Deploys → Trigger deploy → Clear cache and deploy site
```

If your Netlify site name is different, edit `baseURL` in `hugo.toml`.
