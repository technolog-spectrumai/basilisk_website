# Basilisk Systems next-level Hugo design

This patch replaces the old Tailwind/Alpine layout with a fully custom CSS Hugo layout inspired by the premium single-page structure of `Cool_website.html`, but redesigned for Basilisk Systems: autonomous drones, AI perception, secure telemetry, and mission software.

## What changed

- No Tailwind.
- No Alpine.
- No Font Awesome.
- Local static images are served by Hugo from `static/img/`.
- `content/*/index.md` uses `url: "/"`, so pages resolve at `/en/`, `/pl/`, and `/fr/` when `defaultContentLanguageInSubdir = true`.
- The layout has built-in multilingual copy for EN/PL/FR using `.Lang`.

## Apply

From your project root:

```bash
cp -r basilisk_nextlevel_patch/* .
rm -rf public resources
hugo server -D --disableFastRender
```

Open:

```text
http://localhost:1313/en/
http://localhost:1313/pl/
http://localhost:1313/fr/
```

## Important

Your original images were in a root-level `img/` folder. Hugo serves static files from `static/`, so this patch moves them to:

```text
static/img/baz.jpg
static/img/baz_li.png
static/img/logo_b.png
static/img/logo_w.png
```

The template references them as `/img/...` using Hugo `relURL`.
