# HyCanvas (build from source, independent self-host)

Self-host HyCanvas **from source** on this server (local Docker build, bundled Postgres). See [docs/INDEPENDENCE.md](docs/INDEPENDENCE.md).

## Quick start

```bash
# JWT_SECRET in .env (openssl rand -hex 32)
docker compose build
docker compose up -d
```

Open **http://localhost:1669** (or `HYCANVAS_PORT` in `.env`).

## Publicar / clonar o vosso GitHub

Ver [docs/PUBLISH-GITHUB.md](docs/PUBLISH-GITHUB.md). Fork local: [FORK.md](FORK.md).

## Update (após git pull do vosso repositório)

```bash
git pull origin main
docker compose build
docker compose up -d
```

## Stop

```bash
docker compose down
```

## Configuration

| Item | Notes |
|------|--------|
| [`.env`](.env) | `APP_URL` must match public URL |
| [`docker-compose.yml`](docker-compose.yml) | Image `hycanvas-local:production` |
| [`deploy/locales/`](deploy/locales/) | Optional UI strings via `LOCALES_DIR` |

TLS, S3, external Postgres: [DOCKER_SETUP.md](DOCKER_SETUP.md).