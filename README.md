# bapps-workflows

Reusable workflows de GitHub Actions para los repos de bapps. Este repo es público y **nunca lleva secretos**:
los secretos los pasa cada repo que llama, con `secrets: inherit`.

Se llaman siempre con el tag móvil `@v1`.

## Workflows

### `qa.yml`

Valida `bapps.yml` contra `bapps.schema.json` y corre install, lint, test y build (Node y/o Python, se detecta solo).

| Input | Default | Para qué |
|---|---|---|
| `working-directory` | `.` | Carpeta del proyecto |
| `node-version` | `24` | Versión de Node |
| `python-version` | `3.12` | Versión de Python |
| `test-command` | `''` | Pisa la detección (`test:ci`, `test`, `manage.py test`, `pytest`) |
| `manifest-path` | `bapps.yml` | Ruta del manifiesto a validar |

```yaml
jobs:
  qa:
    uses: agusnarvaez/bapps-workflows/.github/workflows/qa.yml@v1
    secrets: inherit
```

### `security.yml`

gitleaks (historial completo, lee `.gitleaksignore`) y osv-scanner.

| Input | Default | Para qué |
|---|---|---|
| `working-directory` | `.` | Carpeta que escanea osv-scanner |

```yaml
jobs:
  security:
    uses: agusnarvaez/bapps-workflows/.github/workflows/security.yml@v1
```

### `selftest.yml`

Prueba los dos de arriba contra los fixtures de `tests/`. No se llama desde afuera.

## `bapps.schema.json`

Generado desde el zod de bapps-console (`pnpm --dir apps/api schema:gen`). No se edita a mano.
