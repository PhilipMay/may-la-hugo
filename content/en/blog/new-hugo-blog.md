---
title: "Migration from Sphinx to Hugo"
date: 2022-07-17
tags:
  - hugo
categories:
  - Blog
---

After a long period of unsatisfaction, I finally found a successor for my [Sphinx](https://www.sphinx-doc.org/) based website.
The primary reason for my dissatisfaction with Sphinx was that it is not possible to integrate a proper blog functionality.
Now you could say that of course there is [ABlog for Sphinx](https://ablog.readthedocs.io/) which provides blog functionality.
However, ABlog seems to me to be poorly maintained. So it says on the [GitHub site](https://github.com/sunpy/ablog#warning):

> This version is maintained with the aim to keep it working for SunPy's website and thus new features or
> bugfixes are highly unlikely from the SunPy maintainers. [...]

![](/img/posts/hugo-logo.svg)

For some time now, I have been considering [Hugo](https://gohugo.io/documentation/).
Especially because it is ranked very high on [Jamstack.org](https://jamstack.org/generators/).
But also because it offers the possibility to integrate documentation and blog with each other.
The only disadvantage of Hugo is that, unlike Sphinx, it cannot be used to document Python code.

After I had decided on Hugo, however, a much more complicated decision now had to be made.
This was which theme I wanted to use.
The theme should not be a pure blog theme. It should make documentation and blog work together.

After some searching and trying I came across [google/docsy](https://www.docsy.dev/docs/).
The functionality seems to be comprehensive and it is sufficiently well maintained.
It is also used to document some other [important projects](https://www.docsy.dev/docs/examples/). Such as:
- <https://www.kubeflow.org/>
- <https://graphviz.org/>
- <https://www.selenium.dev/>
