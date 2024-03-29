---
title: Sphinx
---

## Links
- Sphinx: <https://www.sphinx-doc.org/>
- Sphinx GitHub: <https://github.com/sphinx-doc/sphinx/>
- reStructuredText (reST): <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>
- reStructuredText Primer:
  <https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html>
- Configuration: <https://www.sphinx-doc.org/en/master/usage/configuration.html>
- Table of Contents: <https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html#table-of-contents>
- [Cross-referencing Python objects](https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#python-roles)

## Extensions and Themes
- ABlog: <https://ablog.readthedocs.io/>
- MyST
  - MyST parser: <https://myst-parser.readthedocs.io/>
  - MyST-NB: <https://myst-nb.readthedocs.io/>
- Sphinx Design: <https://sphinx-design.readthedocs.io/>
- markdown-it-py: https://markdown-it-py.readthedocs.io/
- recommonmark: <https://recommonmark.readthedocs.io/>
- Napoleon: <https://www.sphinx-doc.org/en/master/usage/extensions/napoleon.html>
- Read the Docs Sphinx Theme: <https://sphinx-rtd-theme.readthedocs.io/>
- PyData Sphinx Theme: <https://pydata-sphinx-theme.readthedocs.io/>

## Know-how

### Turn warnings into errors
It is possible to turn warnings into errors. This way a build fails when something is wrong.
To do this edit the `Makefile` of Sphinx and change this line:
```
SPHINXOPTS    ?= -W
```
Also see: https://www.sphinx-doc.org/en/master/man/sphinx-build.html#cmdoption-sphinx-build-W

## MyST Syntax
- add a link to a locale PDF or other file - [source](https://github.com/executablebooks/MyST-Parser/issues/341)
```markdown
{download}`text <_static/reference.pdf>`
```

## May.la Installation
- create repo on GitHub and clone it
- chane into the repo directory
- run `sphinx-quickstart` - say yes here:
```text
You have two options for placing the build directory for Sphinx output.
Either, you use a directory "_build" within the root path, or you separate
"source" and "build" directories within the root path.
> Separate source and build directories (y/n) [n]:
```
- delete make.bat - we do not work with windows
- config git with `git config pull.rebase true`
- install https://sphinx-rtd-theme.readthedocs.io/en/latest/
- install https://myst-nb.readthedocs.io/en/latest/
  - add it to extensions
  - turn off notebook building: `jupyter_execute_notebooks = "off"`
- turn off `prev_next_buttons`:
```python
html_theme_options = {
    "prev_next_buttons_location": None,
}
```

## Commands
- convert reStructuredText to Markdown: `pandoc -s -t commonmark -o <target>.md <source>.rst`
