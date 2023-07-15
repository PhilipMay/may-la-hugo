---
title: pyenv
---

## Links
- https://github.com/pyenv/pyenv
- [Command Reference](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)

## Commands
- Python version options:
  - list available Python versions: `pyenv install -l`
  - install new Python version: `pyenv install <version>`
  - uninstall Python version: `pyenv uninstall <version>`
  - list installed Python versions: `pyenv versions`
- update with brew: `brew upgrade pyenv`
- set python version for current directory (and its subdirectories): `pyenv local <version>`

## Set Python Version for new Project
1. list installed Python versions: `pyenv versions`
2. do we want to use one of the versions or install an other?
  - list available Python versions: `pyenv install -l`
  - install new Python version: `pyenv install <version>`
3. set python version for current directory (and its subdirectories): `pyenv local <version>`

## Mac Install
- problems during Python install like `ModuleNotFoundError: No module named '_lzma'` can be fixed with `brew install xz`
