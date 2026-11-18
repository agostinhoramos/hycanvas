# Operating without HyScaler

This instance is built and run **entirely on your hardware**. The HyScaler company, Docker Hub image `hycanvas/hycanvas`, `brand.hycanvas.com`, and `hycanvas.art` are **not** required for the editor, API, auth, or storage.

## What keeps working offline / if HyScaler disappears

| Component | Dependency |
|-----------|------------|
| Editor, exports, realtime | Embedded frontend + Go binary |
| Accounts, designs | Local Postgres + `storage` volume |
| Templates, bundled stock | Embedded catalogs |
| AI features | Your workspace API keys (optional) |

## What needs the public internet (optional)

| Feature | Provider | Disable |
|---------|----------|---------|
| Live photo search | Openverse API | `STOCK_PHOTO_PROVIDER=off` |
| Live icon search | Iconify API | `STOCK_ICON_PROVIDER=off` |
| SMTP, OIDC, S3, AI keys | Your providers | Leave unset |

This stack sets both stock providers to `off` in [`docker-compose.yml`](../docker-compose.yml) so bundled catalog only.

## Checklist

1. **Image** — `docker compose build` (no pull of `hycanvas/hycanvas:latest`).
2. **Secrets** — Stable `JWT_SECRET` in `.env`; rotate only with a session reset plan.
3. **URL** — `APP_URL` and `HYCANVAS_PORT` must match how users reach the app (e.g. `http://localhost:1669`).
4. **Backups** — Docker volumes `pgdata` and `storage` (or bind mounts if you switch).
5. **Source** — Este repositório Git é vosso; ver [PUBLISH-GITHUB.md](PUBLISH-GITHUB.md). Sem remote obrigatório à HyScaler.
6. **Analytics** — Keep `GOOGLE_ANALYTICS_ID` empty unless you opt in.

## Updating

```bash
git pull origin main
docker compose build
docker compose up -d
```

## Legal (brief)

HyCanvas is AGPL-3.0. You may run this fork. The **HyScaler®** trademark is not used on this instance UI; see upstream [`TRADEMARKS.md`](../TRADEMARKS.md) before commercial rebranding.