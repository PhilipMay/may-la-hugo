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
[tool.mypy]
ignore_missing_imports = true
```
