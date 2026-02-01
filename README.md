# model-template
A lightweight template repo for building and shipping model-backed services in the Homebrain AI ecosystem. This repo is intended to be used as a starting point for new model projects. It comes pre-wired to our platform CI/security workflows so you don’t have to reinvent pipelines.

## Workflows You Get
Triggers on push to `main` (ideally only accepted PR's)
1. `run-ci.yml`
    * PR to main → runs
2. `security.yml`
    * PR to main → runs
    * Runs against main every Monday.
3. `build-image.yml`
    * PR to main → checks build, no push. 
    * Merge/push to main → build + push. 
    * Manual run → build + push
4. `deploy.yml`
    * Manual run → deploys

## Repo Structure
```bash
.
├─ app/                 # application code
├─ tests/               # model tests
├─ artifacts/           # model artifacts (usually ignored in git; use a registry/storage to store/pull artifacts)
├─ pyproject.toml       # dependencies + tool config
├─ Dockerfile           # if you ship as an image
└─ .github/workflows/   # workflows that call platform workflows in infra repo
```

## Local dev quickstart

### Create Virtual Env
```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -U pip
```

### Install dependencies
```bash
python -m pip install -r requirements.txt
```

### Formatting, Lint, and Typecheck, Tests
```bash
# Formatting
ruff format .
# Lint
ruff check .
# Typechecks
pyright
# Run Python tests
python -m pytest -q
```
