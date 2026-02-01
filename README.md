# model-template
A lightweight template repo for building and shipping model-backed services in the Homebrain AI ecosystem. This repo is intended to be used as a starting point for new model projects. It comes pre-wired to our platform CI/security workflows so you don’t have to reinvent pipelines.

## What you get
Triggers on push to `main` (ideally only accepted PR's)
* `run-ci.yml` - 
* `security.yml` - 
* `build-image.yml` - 
* `deploy.yml` - 

## Repo Structure
```bash
.
├─ app/                 # application code
├─ tests/               # pytest tests
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