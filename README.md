# Basilisk Netlify prebuilt fallback

This package avoids the Netlify Hugo installer/GitHub rate-limit issue by publishing the already generated `public/` directory.

## Apply

```bash
unzip basilisk_netlify_prebuilt.zip
cp -r basilisk_netlify_prebuilt/* .
git add .
git commit -m "Use prebuilt Netlify deploy output"
git push
```

## Important

In Netlify UI, remove any `HUGO_VERSION` environment variable if you are using this prebuilt mode. The build command does not run Hugo; it only publishes `public/`.

Later, when GitHub rate limits are gone, you can switch back to:

```toml
[build]
  command = "hugo --minify"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.148.2"
```
