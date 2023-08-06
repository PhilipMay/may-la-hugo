---
title: Poetry
---

## Links
- https://python-poetry.org/docs/
  - [Commands](https://python-poetry.org/docs/cli/)
  - [Configuration](https://python-poetry.org/docs/configuration/)
  - [Dependency specification (version constraints)](https://python-poetry.org/docs/dependency-specification/)
  - [The pyproject.toml file](https://python-poetry.org/docs/pyproject/)

## Commands
- initialize a pre-existing project: `poetry init`
- add package: `poetry add <package>`
- install current project with dependencies: `poetry install`
- publish (and build) to PyPI: `poetry publish --build -u <username> -p <password>`

## Dependency Groups & Extras
- To declare a set of dependencies, which add additional functionality to the project during runtime, use extras instead.
- add dependency: `poetry add <package>`
- add dependency in a group (lint, test, etc.): `poetry add --group <group> <package>`
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
- always copy python into `venv`: `poetry config virtualenvs.options.always-copy true`
- `poetry config virtualenvs.prefer-active-python true`
- config file on Mac: `~/Library/Application\ Support/pypoetry/config.toml`
- Poetry directories on Mac:
  - `~/Library/Caches/pypoetry`
  - `~/Library/Application\ Support/pypoetry`
  - `~/.local/bin` with a symlink to the poetry executable

### Lint Example
```toml
[tool.poetry.group.lint.dependencies]
black = "*"
ruff = "*"
mypy = "*"

[tool.black]
line-length = 119
target-versions = ["py38", "py39", "py310", "py311"]

[tool.ruff]
select = [
  "E",  # pycodestyle
  "F",  # pyflakes
  "I",  # isort
]
line-length = 119
fixable = ["I"]
target-version = "py38"

[tool.mypy]
ignore_missing_imports = true
```

## FAQ
- Where is the Poetry cache dir at Mac? `~/Library/Application Support/pypoetry`
