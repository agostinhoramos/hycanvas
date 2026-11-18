# HyCanvas (build from source, independent self-host)

Self-host HyCanvas **from source** on this server. Public URL: **https://cr.newgus.com/hycanvas/** (nginx subpath).

See [docs/INDEPENDENCE.md](docs/INDEPENDENCE.md) and [deploy/nginx-subpath.example.conf](deploy/nginx-subpath.example.conf).

## Quick start

```bash
docker compose build    # BASE_PATH=/hycanvas is baked into the image
docker compose up -d
```

Direct port (debug): `http://localhost:1669` — production users use the HTTPS URL above.

## Reverse proxy requirements

- `APP_URL` and `FRONTEND_URL` = `https://cr.newgus.com/hycanvas` (no trailing slash)
- `BASE_PATH=/hycanvas`, `COOKIE_SECURE=true`
- nginx must forward WebSocket upgrades (`/hycanvas/realtime`)

## Update

```bash
git pull origin main
docker compose build
docker compose up -d
```

## Publicar no GitHub

[docs/PUBLISH-GITHUB.md](docs/PUBLISH-GITHUB.md)

## Stop

```bash
docker compose down
```