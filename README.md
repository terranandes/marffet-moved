# marffet-moved

A one-file static notice served on the retired host **`marffet-app.zeabur.app`**,
pointing visitors at the current one: **<https://35-236-152-123.sslip.io>**.

This repo contains no application code and no data. It exists only so the old
subdomain keeps answering with something useful instead of going dark.

## Contents

| File | Purpose |
| --- | --- |
| `index.html` | The entire site. Self-contained: inline CSS, inline script, no external assets, no fonts, no trackers. |

## How it is deployed

Zeabur static site (Caddy). Zeabur serves `index.html` for any path it cannot
find on disk, so deep links kept in old bookmarks (`/etf`, `/portfolio`, ...)
reach the notice rather than a 404. A small inline script appends the arriving
path to the outbound link, so `/etf` on the old host offers
`https://35-236-152-123.sslip.io/etf`.

Deliberately **no** `404.html`: adding one would take priority over the
index-fallback and would show a 404 page on exactly those deep links.

## If a hard redirect is wanted instead of a notice page

Zeabur supports a Netlify-style `_redirects` file. Replacing the notice with a
301 would be:

```
/*  https://35-236-152-123.sslip.io/:splat  301
```

That is intentionally not enabled — the visible notice is the chosen behaviour,
so visitors learn the address changed instead of being moved silently.
