# Fork patches (self-host)

Local changes on top of HyCanvas (AGPL-3.0) for independent operation: no HyScaler CDN/SaaS, build-from-source compose, optional locale overrides.

## Patched files

| File | Change |
|------|--------|
| [`docker-compose.yml`](docker-compose.yml) | Local build, `LOCALES_DIR`, stock off |
| [`.env`](.env) | `APP_URL`, independence flags |
| [`frontend/src/pages/_document.tsx`](frontend/src/pages/_document.tsx) | On-instance OG images |
| [`frontend/src/components/auth/AuthForm.tsx`](frontend/src/components/auth/AuthForm.tsx) | Optional footer line |
| [`frontend/src/components/editor/PublishDialog.tsx`](frontend/src/components/editor/PublishDialog.tsx) | No SaaS URL fallback |
| [`frontend/src/components/installation/Step1Access.tsx`](frontend/src/components/installation/Step1Access.tsx) | Generic proxy placeholder |
| Locales under [`frontend/`](frontend/) | HyScaler footer cleared |
| [`backend/internal/stock/`](backend/internal/stock/) | Generic User-Agent |
| [`deploy/locales/`](deploy/locales/) | Runtime locale overrides |

## Verification

```bash
rg -i 'hyscaler|hycanvas\.art|brand\.hycanvas' \
  frontend/src backend/internal docker-compose.yml .env deploy \
  --glob '!**/*_test.go'
```

Runtime paths should not reference HyScaler hosts (key names may still contain `hyscaler`).