# Cricket Cards images

Static hosting (GitHub Pages) for the player images used by the Cricket Cards app. These files were
previously served from Supabase Storage (bucket `cricket-players`).

## URL mapping

The path under the host is the same as the Supabase public-object path, so the app's image resolver
(which keys off the path, not the host) works unchanged:

```
https://<supabase-project>.supabase.co/storage/v1/object/public/cricket-players/<object>
https://ijaz529.github.io/cricket-cards-images/storage/v1/object/public/cricket-players/<object>
```

Folders under `cricket-players/`:

- `headshots/`, `photos/`: original player photos
- `headshots-384/`, `headshots-1024/`, `photos-384/`, `photos-1024/`: the same images resized to 384 or 1024 px wide
- top level: card art. Files over 300 KB were re-encoded to save space, with the same name, extension and pixel
  size. JPEGs use quality 82, and PNGs are lossless.

## Licences

Many player photos are Creative Commons or public-domain images (mostly from Wikimedia Commons). Each one is
credited, with its licence, on the credits page:
https://ijaz529.github.io/cricket-cards-site/credits.html

Those images remain under their original licences. Nothing in this repository grants any other licence.

## Older app builds

App builds up to iOS 1.1.6 / Android versionCode 37 request images from Supabase's resize endpoint
(`/storage/v1/render/image/public/cricket-players/<object>?width=...`). `storage/v1/render/image/public/` holds a
static copy for them at 384 px wide (the query string is ignored): `headshots/` and `photos/` are the `-384`
variants, and the card art is resized to 384 px wide.
