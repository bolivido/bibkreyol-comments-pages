# bibkreyol-comments-pages (bolivido)

Second **GitHub Pages** mirror for BibKreyol daily comment JSON, under [github.com/bolivido](https://github.com/bolivido).

## Read URL pattern

`https://bolivido.github.io/bibkreyol-comments-pages/comments/daily/{yyyy-MM-dd}.json`

Same path shape as Firebase Hosting, Cloudflare Pages, and [bolividob/bibkreyol-comments-data](https://github.com/bolividob/bibkreyol-comments-data).

## Deploy

- **GitHub Actions** (`.github/workflows/deploy-github-pages.yml`) publishes on every push that changes `comments/daily/**`, `_headers`, or `_routes.json`.
- **Settings → Pages** must use **GitHub Actions** as the source (enabled automatically via API on first setup).

## Content

Keep `comments/daily/*.json` in sync with your compaction output (e.g. copy from `bibkreyol-comments-data` or automate in CI). Root `_headers` / `_routes.json` match the BibKreyol Cloudflare Pages static doc for repos also connected to Cloudflare.
