---
title: Linter
---

## Black
- see https://black.readthedocs.io/
- ignore formatting in one line: `# fmt: skip`

## mypy
- see https://mypy.readthedocs.io/
- ignore all checks in one line: `# type: ignore`
- ignore specific check in one line: `# type: ignore[check-name]`

## Ruff
- see https://beta.ruff.rs/docs/
- ignore formatting in one line: `# noqa: id_to_ignore`

## Useful `pyproject.toml` Config

```toml
[tool.poetry.group.lint.dependencies]
black = "*"
ruff = "*"
mypy = "*"
mdformat = "*"

[tool.black]
line-length = 119
target-versions = ["py38", "py39", "py310", "py311"]

[tool.ruff]
select = [
  "E",  # pycodestyle
  "F",  # pyflakes
  "I",  # isort
  "D",  # pydocstyle
]
line-length = 119
fixable = ["I"]
target-version = "py38"
ignore = [
  "D107",  # Missing docstring in `__init__`
  "D410",  # Missing blank line after section ("Args")
  "D411",  # Missing blank line before section ("Returns")
]

[tool.ruff.per-file-ignores]
"tests/**/test_*.py" = [
  "D100",
  "D103",
]

[tool.ruff.pydocstyle]
convention = "google"

[tool.mypy]
ignore_missing_imports = true
```
