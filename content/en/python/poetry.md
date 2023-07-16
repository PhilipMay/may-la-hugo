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

## Dependency Groups & Extras
- To declare a set of dependencies, which add additional functionality to the project during runtime, use extras instead.
- add dependency: `poetry add <package>`
- add optional dependency: `poetry add --optional <package>`

There currently is no support for making optional packages part of a specific group during their addition.
You have to maintain this section in the `pyproject.toml` file by hand:
```
[tool.poetry.extras]
<group_name> = ["package"]
```

## Config
- see locale config: `poetry config --list`
- store env. in locale project in `.venv`: `poetry config virtualenvs.in-project true --local`
  - see https://python-poetry.org/docs/configuration/#virtualenvsin-project
  - this creates a `poetry.toml` file in the locale project when it is not available
- config file on Mac: `~/Library/Application\ Support/pypoetry/config.toml`

## FAQ
- Where is the Poetry cache dir at Mac? `~/Library/Application Support/pypoetry`
