---
title: Poetry
---

## Links
- https://python-poetry.org/docs/
  - [Commands](https://python-poetry.org/docs/cli/)
  - [Configuration](https://python-poetry.org/docs/configuration/)
  - [Dependency specification (version constraints)](https://python-poetry.org/docs/dependency-specification/)

## Commands
- initialize a pre-existing project: `poetry init`
- add package: `poetry add <package>`
- install current project with dependencies: `poetry install`
- publish (and build) to PyPI: `poetry publish --build -u <username> -p <password>`

## Config
- see locale config: `poetry config --list`
- store env. in locale project in `.venv`: `poetry config virtualenvs.in-project true --local`
  - see https://python-poetry.org/docs/configuration/#virtualenvsin-project
  - this creates a `poetry.toml` file in the locale project when it is not available

## FAQ
- Where is the Poetry cache dir at Mac? `~/Library/Application Support/pypoetry`
