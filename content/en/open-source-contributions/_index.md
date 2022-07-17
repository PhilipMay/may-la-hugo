---
title: "My Open Source Contributions"
linkTitle: "Open Source Contributions"
cascade:
- type: "docs"
weight: 60
menu:
  main:
    weight: 60
---

## Projects

[HPOflow](https://github.com/telekom/HPOflow)<br/>
Tools for [Optuna](https://optuna.readthedocs.io/),
[MLflow](https://www.mlflow.org/docs/latest/index.html) and
the integration of both

[XLSR – Cross-Lingual Sentence Representations](https://github.com/German-NLP-Group/xlsr)

[Transformer-Tools](https://github.com/telekom/transformer-tools)<br/>
Tools for [Hugging Face / Transformers](https://github.com/huggingface/transformers)

[Lazy-Imports](https://github.com/telekom/lazy-imports)<br/>
Python tool to support lazy imports

[ML-Cloud-Tools](https://github.com/telekom/ml-cloud-tools)

[Census-Income with LightGBM and Optuna](https://github.com/telekom/census-income-lightgbm)

[Style-Doc](https://github.com/telekom/style-doc)

[PyCharm Community Edition IDE for Python with bundled JRE](https://aur.archlinux.org/packages/pycharm-community-jre)<br/>
An [Arch Linux](https://archlinux.org/) package ([AUR](https://wiki.archlinux.org/title/Arch_User_Repository))

## Models

[T-Systems-onsite/cross-en-de-roberta-sentence-transformer](https://huggingface.co/T-Systems-onsite/cross-en-de-roberta-sentence-transformer)

[german-nlp-group/electra-base-german-uncased](https://huggingface.co/german-nlp-group/electra-base-german-uncased)
joined work with [Philipp Reißel](https://twitter.com/phil_ipp_)
([ambeRoad](https://amberoad.de/))

[T-Systems-onsite/mt5-small-sum-de-en-v2](https://huggingface.co/T-Systems-onsite/mt5-small-sum-de-en-v2)

## Pull Requests

[Hugging Face / Transformers](https://github.com/huggingface/transformers)
- add classifier_dropout to classification heads: [#12794](https://github.com/huggingface/transformers/pull/12794)
- add option for subword regularization in sentencepiece tokenizer: [#11149](https://github.com/huggingface/transformers/pull/11149),
[#11417](https://github.com/huggingface/transformers/pull/11417)
- add strip_accents to basic BertTokenizer: [#6280](https://github.com/huggingface/transformers/pull/6280)
- refactor slow sentencepiece tokenizers and add tests: [#11716](https://github.com/huggingface/transformers/pull/11716),
[#11737](https://github.com/huggingface/transformers/pull/11737)
- [more fixes and improvements](https://github.com/huggingface/transformers/pulls?q=is%3Apr+author%3APhilipMay)

[Optuna](https://github.com/optuna/optuna)
- add MLflow integration callback: [#1028](https://github.com/optuna/optuna/pull/1028)
- trial level suggest for same variable with different parameters give warning: [#908](https://github.com/optuna/optuna/pull/908)
- [more fixes and improvements](https://github.com/optuna/optuna/pulls?q=is%3Apr+author%3APhilipMay)

[Sentence Transformers](https://github.com/UKPLab/sentence-transformers)
- add callback so we can do pruning and check for nan values: [#327](https://github.com/UKPLab/sentence-transformers/pull/327)
- add option to pass params to tokenizer: [#342](https://github.com/UKPLab/sentence-transformers/pull/342)
- always store best_score: [#439](https://github.com/UKPLab/sentence-transformers/pull/439)
- fix for OOM problems on GPU with large datasets: [#525](https://github.com/UKPLab/sentence-transformers/pull/525)

## Datasets

[NLU Evaluation Data – German and English + Similarity](https://github.com/t-systems-on-site-services-gmbh/NLU-Evaluation-Data-de-en)

[The German colossal, cleaned Common Crawl corpus (GC4 corpus)](https://german-nlp-group.github.io/projects/gc4-corpus.html)<br/>
joined work with [Philipp Reißel](https://twitter.com/phil_ipp_)
([ambeRoad](https://amberoad.de/))
