---
title: PIP
---

## Install Packages
- install GIT development code: `pip install git+<https_git_clone_link>`
- install GIT development code from branch: `pip install git+<https_git_clone_link>@<branch_name>`
- install editable local Projects:
  - `pip install -e .`
  - also see <https://pip.pypa.io/en/stable/reference/pip_install/#editable-installs>

## List Packages
- list outdated packages: `pip list -o`
- list packages in requirements.txt format: `pip list --format freeze`

## Other Commands
- delete package cache: `pip cache purge`

## Install and update Packages from a File
For pip you can create so called [requirements
files](https://pip.pypa.io/en/stable/user_guide/#requirements-files).
These files just list one package per line. Packages from this file can
be installes with `pip install -r <requirements.txt>` and updatet
with `pip install -r <requirements.txt> -U`. The update only makes
sence when you do not specify a version number with the package.

Since pip does not support an “update all” mechanism this is a good way
to install and update the needed packages.

To add a package from GIT just add `git+<https_git_clone_link>` instead of the normal package name.

## Build PyPI Packages
- Python Packaging User Guide: <https://packaging.python.org/>
- Packaging Python Projects:
  <https://packaging.python.org/tutorials/packaging-projects/>
- Writing the Setup Script:
  <https://docs.python.org/3.6/distutils/setupscript.html>
- Classifiers: <https://pypi.org/classifiers/>
- PEP 440 - Version Identification and Dependency Specification:
  <https://www.python.org/dev/peps/pep-0440/>
- twine’s documentation: <https://twine.readthedocs.io/en/latest/>
- install_requires:
  <https://setuptools.readthedocs.io/en/latest/setuptools.html?highlight=python_requires#declaring-dependencies>
- python_requires:
  <https://setuptools.readthedocs.io/en/latest/setuptools.html?highlight=python_requires#new-and-changed-setup-keywords>
- setup.py Beispiele:
  - Tensorflow:
    <https://github.com/tensorflow/tensorflow/blob/6729cd7d1c07e547298fa2a02d1e36390dc62f0a/tensorflow/tools/pip_package/setup.py>
  - NumPy: <https://github.com/numpy/numpy/blob/master/setup.py>
  - pandas: <https://github.com/pandas-dev/pandas/blob/master/setup.py>
- Kurzanleitung pip Paket erstellen und zu PyPI hochladen: ``python3 setup.py sdist bdist_wheel`` - ``twine upload dist/*``
