---
title: Poetry
---

## Links
- https://python-poetry.org/docs/

## Config
- see locale config: `poetry config --list`
- store env. in locale project in `.venv`: `poetry config virtualenvs.in-project true --local`
  - see https://python-poetry.org/docs/configuration/#virtualenvsin-project
  - this creates a `poetry.toml` file in the locale project when it is not available

## FAQ
- Where is the Poetry cache dir at Mac? `~/Library/Application Support/pypoetry`
