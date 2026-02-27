# git-templates

Opinionated project templates for Python backend services. Copy what you need, fill the `[PLACEHOLDERS]`, delete what you don't.

## What's included

| File | Purpose |
| ---- | ------- |
| `README.template.md` | Project README with quickstart, usage, config, testing |
| `ARCHITECTURE.template.md` | Architecture spec (domain, layers, APIs, observability, ...) |
| `CHANGELOG.template.md` | Keep a Changelog format + SemVer |
| `pyproject.template.toml` | Python metadata, deps, ruff, pytest, mypy, coverage config |
| `Dockerfile.template` | Multi-stage build (builder + runtime), uv, non-root, healthcheck |
| `docker-compose.template.yaml` | app + PostgreSQL + Redis + optional Traefik proxy |
| `.env-compose.template` | Environment variables for Docker Compose |
| `Makefile.template` | Developer shortcuts (uv sync, lint, test, docker build) |
| `pre-commit.template.yaml` | Pre-commit hooks: ruff, mypy, file checks, gitleaks |
| `.github/workflows/ci.template.yml` | GitHub Actions CI: lint, test, optional Docker build |
| `.dockerignore.template` | Excludes for Docker build context |
| `.gitignore.template` | Git ignores: caches, venvs, secrets, IDE files |
| `.env.template` | Placeholder for local dev env vars |


## Stack (default)

- **Python** >= `[PYTHON_VERSION]` (default 3.12 in Dockerfile)
- **uv** as package/project manager
- **Ruff** for linting + formatting
- **Mypy** for type checking
- **Pytest** for testing
- **Docker** + Compose for containerization
- **PostgreSQL** + **Redis** as default services

Not using one of these? Delete the relevant sections — the templates are designed to be trimmed.

## Conventions

- All placeholders use `[UPPERCASE_BRACKETS]` syntax
- All text in English
- Exhaustive inline comments in `Dockerfile`, `docker-compose.yaml`, and `pyproject.toml` (look for `↑` arrows)
- Minimal filler — structure over prose
