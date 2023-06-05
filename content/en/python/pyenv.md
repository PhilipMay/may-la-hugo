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
- set python version for current directory (or its subdirectories): `pyenv local <version>`

## Mac Install
- problems during Python install like `ModuleNotFoundError: No module named '_lzma'` can be fixed with `brew install xz`
