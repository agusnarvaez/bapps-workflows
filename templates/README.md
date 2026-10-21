# Plantillas

Cada repo las copia y reemplaza los placeholders. Guía completa: `docs/estandar/onboarding-proyecto.md` en bapps-console.

| Placeholder | Qué es | Ejemplo |
|---|---|---|
| `ID` | id del proyecto (`^[a-z0-9-]+$`) | `canastita` |
| `URL_TESTING` | URL del sitio de testing, sin barra final | `https://canastita-testing.bapps.com.ar` |
| `URL_PROD` | URL de prod, sin barra final | `https://canastita.com.ar` |
| `BUILD_DIR` | carpeta que se publica | `dist` |

| Plantilla | Va a | Notas |
|---|---|---|
| `ci.yml`, `deploy-testing.yml`, `deploy-prod.yml`, `release.yml` | `.github/workflows/` | `deploy-prod.yml` nunca lleva `push:` |
| `dependabot.yml` | `.github/dependabot.yml` | `pip` en vez de `npm` en repos Python |
| `release-please-config.json` | raíz | `release-type`: `node`, `python`, o `simple` sin `pyproject.toml` |
| `.release-please-manifest.json` | raíz | versión actual del proyecto |
| `CLAUDE.md` | raíz | sección dotclaude (harness). Si el repo ya tiene `CLAUDE.md` o `AGENTS.md`, pegar sólo la sección |
