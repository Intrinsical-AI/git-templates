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


## Stack (default) — opinionated by design

These templates ship with a specific stack because **good defaults beat endless configuration**. Instead of abstracting over every possible database, cache, or CI provider, we picked one well-understood option per layer and documented it thoroughly. The result: you get a working setup in minutes, not hours.

| Layer | Default | Why |
| ----- | ------- | --- |
| Language | Python >= `[PYTHON_VERSION]` | Target audience. 3.12+ for modern syntax & performance |
| Package manager | uv | Fast, deterministic, replaces pip + pip-tools + venv |
| Lint + format | Ruff | Single tool replaces black, isort, flake8, pyupgrade |
| Type checking | Mypy | Most mature Python type checker, wide ecosystem support |
| Testing | Pytest | De facto standard, rich plugin ecosystem |
| Containers | Docker + Compose | Industry standard for local dev and deployment |
| Database | PostgreSQL 16 | Most capable open-source RDBMS, strong defaults |
| Cache / broker | Redis 7 | Ubiquitous in-memory store, minimal config |
| CI | GitHub Actions | Largest hosted CI platform, native to GitHub repos |

**Using a different database, cache, or service?** Delete or replace the relevant sections — the templates are designed to be trimmed, not to be a universal abstraction layer. Opinionated starters get you running; your project's needs dictate what stays.

## Conventions

- All placeholders use `[UPPERCASE_BRACKETS]` syntax
- All text in English
- Exhaustive inline comments in `Dockerfile`, `docker-compose.yaml`, and `pyproject.toml` (look for `↑` arrows)
- Minimal filler — structure over prose
