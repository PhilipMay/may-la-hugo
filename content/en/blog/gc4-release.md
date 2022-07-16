---
title: "German colossal, cleaned Common Crawl corpus (GC4) released"
date: 2021-04-10
tags:
  - german-data
  - text-corpus
  - common-crawl
categories:
  - Data
  - NLP
---

[Philipp Reißel](https://twitter.com/phil_ipp_) ([ambeRoad](https://amberoad.de/)) and
me published the largest German text corpus within the German NLP Group:
[The German colossal, cleaned Common Crawl corpus](https://german-nlp-group.github.io/projects/gc4-corpus.html)

![](/img/posts/common-crawl.png)

GC4 is a German text corpus based on [Common Crawl](https://commoncrawl.org/).
It has been cleaned and preprocessed and can be used for various tasks in NLP.
For example for self-supervised training of language models.

The text corpus has the size of 454 GB packed.
Unpacked it is more than 1 TB. This makes it the largest German language corpus.
For comparison, the complete German Wikipedia pages are about 6.5 GB of text.
The preprocessing took more than 50,000 CPU hours and
about 400 TB of network traffic to the Common Crawl S3 bucket.

Many thanks to [iisys (the Institute of Information Systems Hof University)](https://www.iisys.de/) for hosting this dataset.
