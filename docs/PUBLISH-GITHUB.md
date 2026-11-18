# Publicar neste GitHub

Este directório é um repositório Git **autónomo** (sem remote da HyScaler). Código derivado de HyCanvas (AGPL-3.0); mantenha `LICENSE` e `NOTICE` no repositório.

## Primeira publicação

```bash
cd /caminho/para/hycanvas

# Criar repo vazio no GitHub (via web UI), depois:
git remote add origin https://github.com/<UTILIZADOR>/<REPO>.git
git push -u origin main
```

Com SSH:

```bash
git remote add origin git@github.com:<UTILIZADOR>/<REPO>.git
git push -u origin main
```

## Commits seguintes

```bash
git add -A
git commit -m "Descrição da alteração"
git push
```

## Deploy no servidor

```bash
docker compose build
docker compose up -d
```

Não é necessário `git pull` de terceiros; só do vosso `origin`.