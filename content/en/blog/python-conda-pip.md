---
title: "Python Installation and Package Management with conda and pip"
date: 2022-07-23
tags:
  - conda
  - pip
categories:
  - Python
---

This article is about installing Python and package management.
It is a subjective article and represents my own opinion and experience.
The article is structured by several recommendations.

## Recommendation 1: Never install Python
This sounds a bit strange but the first recommendation is to never install Python itself.
The reason is that otherwise you would commit to a single very concrete Python version.
However, you don't want that in principle, because there are different packages that have
different version requirements.

But how do you install Python without installing it?

## Recommendation 2: Use conda to install and manage Python
You should use [conda](https://docs.conda.io/) to install and manage Python:

> Conda is an open source package management system and environment management system that
> runs on Windows, macOS, Linux and z/OS.

To install conda you use [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

After installation, conda can now be used to create various so-called environments.
In each of these environments you can install a different Python version.
In addition, you can install other Python packages in the environments.
You can switch between the environments with a single command and you can also delete them
easily if necessary.

More details about the use and installation of conda you can find on my
[conda page](/python/conda/).

## Recommendation 3: Disable conda automatic base Activation
After the conda installation, the so-called base environment is automatically activated in every shell.
If you now install a package - without explicitly activating another environment before - then
the package will be installed into this base environment. This clutters up the base environment and
is annoying. So to force an explicit environment activation you can disable conda automatic base activation.
This is done with the following command: `conda config --set auto_activate_base false`

## Recommendation 4: Never install Anaconda
Anaconda also includes conda. During the installation, however, numerous other packages are installed
completely unnecessarily. This is the reason why Anaconda is just an unnecessary and
completely bloated software that I cannot recommend to anyone.
Nothing more needs to be said about this.

## Recommendation 5: Do not use conda to install Packages
Conda can be used not only to manage environments and
different Python versions, but also to install Python packages like NumPy or pandas.

Very soon after I started with Python and Data Science,
I wrote the first bug reports for different Python packages.
So when you write such a bug report the maintainers also ask for the used version.
When I wrote "conda package version x.y" I always got the following knee-jerk answer:
"Please install the *pip* version x.y of the package and try again."

The reason is that the conda packages are potentially completely different from the pip packages.
Many maintainers release only unofficially or not at all a conda version of their software.
Then the conda package is maintained by someone completely different.

## Recommendation 6: Use pip to install Packages
To avoid the problem described above, I always use [pip](https://pip.pypa.io/en/stable/)
for package installation.
Conda is then only used to create and manage the environments and to install Python.
In some places on the internet you can find that there might be problems if you combine pip and conda.
I can not confirm this.
