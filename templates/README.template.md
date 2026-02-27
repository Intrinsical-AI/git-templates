
# [PROJECT_NAME]

<!-- [![CI](...)](#) [![Coverage](...)](#) [![License](...)](#) -->

> [ONE_LINER]: what it is, who it's for, and the outcome it produces.

## Status

| Field         | Value                          |
| ------------- | ------------------------------ |
| Status        | Draft / Active / Maintenance / Deprecated |
| Latest release| `v[X.Y.Z]` ([RELEASE_DATE])   |
| Compatibility | Python `>=[PYTHON_VERSION]`    |
| Support       | [SUPPORT_CHANNEL]              |

---
d

## What is this

[2-6 LINES]: describe the problem it solves, the approach, and the output (API, CLI, library, job, etc.).

### Features

- [FEATURE_1]
- [FEATURE_2]
- [FEATURE_3]

### Use cases (and anti-cases)

**Use it if:**
- ...

**Don't use it if:**
- ...

---

## Goals and non-goals

### Goals
1. ...
2. ...

### Non-goals
- ...

### Constraints
- Performance: [CONSTRAINT]
- Consistency: [CONSTRAINT]
- Compliance: [CONSTRAINT]
- Cost: [CONSTRAINT]
- Security: [CONSTRAINT]

---

## Quickstart

### Option A — Local (no Docker)

```bash
uv sync
[COMMAND_TO_RUN]
```

### Option B — Docker Compose

```bash
cp .env.example .env    # edit with your values
docker compose up -d --build
docker compose logs -f app
```

---

## Installation

### As a library

```bash
uv add [PROJECT_SLUG]
```

### As a CLI tool

```bash
uv tool install [PROJECT_SLUG]
[PROJECT_SLUG] --help
```

---

## Usage

### Minimal example

```python
from [PACKAGE] import [THING]

[THING].run(...)
```

### CLI example

```bash
[PROJECT_SLUG] serve --port 8000
```

### API

- OpenAPI docs: `http://localhost:[PORT]/docs`
- Key endpoints:
  - `GET /health`
  - `POST /[ENDPOINT]`

---

## Configuration

> Rule: **config per environment** (dev/staging/prod). Avoid dangerous defaults.

### Environment variables

| Variable     | Example      | Required | Purpose       |
| ------------ | ------------ | -------: | ------------- |
| `APP_ENV`    | `production` |      Yes | Runtime mode  |
| `APP_PORT`   | `8000`       |      Yes | Listen port   |
| `DB_URL`     | `...`        |  Depends | Database      |

### Secrets

- Local dev: `secrets/*.txt` (do NOT commit)
- Prod: secret manager (KMS / Vault / etc.)

---

## Architecture

### Repo layout

```
[PACKAGE]/          # flat layout (default)
  domain/
  application/
  adapters/
tests/
docs/
  architecture.md
  adr/
docker-compose.yaml
```

### Invariants

- [INVARIANT_1]
- [INVARIANT_2]

---

## Development

### Requirements

- [uv](https://docs.astral.sh/uv/) (recommended) or Python `>=[PYTHON_VERSION]`
- Docker (optional)

### Useful commands

```bash
uv run ruff check . && uv run ruff format .   # lint + format
uv run mypy .                                  # type check
uv run pytest -q                               # test
# or: make lint / make type / make test
```

### Conventions

- [NAMING_STYLE]
- [DEPENDENCY_POLICY]

---

## Testing

| Type        | Path                | Coverage target |
| ----------- | ------------------- | --------------: |
| Unit        | `tests/unit/`       |          [PCT]% |
| Integration | `tests/integration/`|          [PCT]% |
| E2E         | `tests/e2e/`        |          [PCT]% |

---


## Roadmap

- [ ] [MILESTONE_1]
- [ ] [MILESTONE_2]

---

## Contributing

[CONTRIBUTING_GUIDELINES]

---

## License

[LICENSE]
