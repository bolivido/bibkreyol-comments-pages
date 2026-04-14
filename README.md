# bibkreyol-comments-pages (bolivido)

Second **GitHub Pages** mirror for BibKreyol daily comment JSON, under [github.com/bolivido](https://github.com/bolivido).

## Read URL pattern

`https://bolivido.github.io/bibkreyol-comments-pages/comments/daily/{yyyy-MM-dd}.json`

Same path shape as Firebase Hosting, Cloudflare Pages, and [bolividob/bibkreyol-comments-data](https://github.com/bolividob/bibkreyol-comments-data).

## Deploy

- **GitHub Actions** (`.github/workflows/deploy-github-pages.yml`) publishes on every push that changes `comments/daily/**`, `_headers`, or `_routes.json`.
- **Settings → Pages** must use **GitHub Actions** as the source (enabled automatically via API on first setup).

## Content (automatic sync)

**`sync-from-comments-data.yml`** copies `comments/daily/*.json` from **[bolividob/bibkreyol-comments-data](https://github.com/bolividob/bibkreyol-comments-data)** into this repo and pushes. That triggers **`deploy-github-pages.yml`** so `https://bolivido.github.io/bibkreyol-comments-pages/...` updates.

| Trigger | When |
|---------|------|
| **Every 10 minutes** (schedule) | Pulls from upstream `main` — no secret needed |
| **workflow_dispatch** | Manual “Run workflow” |
| **repository_dispatch** `sync-comments-data` | Fired from upstream repo when you add optional PAT (see below) |

### Optional: push-to-push sync from `bibkreyol-comments-data`

In **bolividob/bibkreyol-comments-data** → **Settings → Secrets**, add **`BOLIVIDO_MIRROR_DISPATCH_TOKEN`**: a GitHub PAT from the **bolivido** account with permission to call `repository_dispatch` on `bolivido/bibkreyol-comments-pages`. Then each push to `comments/daily/**` on `main` runs **`trigger-bolivido-pages-mirror.yml`** and notifies this repo immediately (otherwise the 10-minute schedule still applies).

Root `_headers` / `_routes.json` match the BibKreyol Cloudflare Pages static doc for repos also connected to Cloudflare.
