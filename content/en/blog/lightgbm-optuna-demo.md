---
title: "LightGBM with Optuna: Demo released"
date: 2022-02-20
tags:
  - hyperparameter
  - lightgbm
  - optuna
categories:
  - Gradient Boosted Trees
---

This week I published a project to show how to combine
LightGBM and Optuna efficiently to train good models.
The purpose of this work is to be able to be reused as a template for new projects.

![](/img/posts/lightgbm-optuna.png)

**LightGBM** is a library that uses gradient-boosted tree-based learning algorithms to train models on flat data.
Compared to neural networks, it is very fast and not worse for many use cases.
It is my preferred supervised learning tool for tabular data.
So basically all data that are not images, time series or texts.

**Optuna** is a framework for automatic hyperparameter optimization.
Optuna is my favorite tool for hyperparameter optimization.
The dataset used is the [census income data](https://archive-beta.ics.uci.edu/ml/datasets/census+income).
The task is to predict whether income exceeds $50K/yr.

On top of that we apply the
[SignificanceRepeatedTrainingPruner](https://telekom.github.io/HPOflow/doc/SignificanceRepeatedTrainingPruner.html#significancerepeatedtrainingpruner-doc).
This is a tool to detect bad hyperparameter sets as early as possible during cross validation.
Thus, the cross validation can be aborted at an early stage and does not have to be run through completely.
This procedure is commonly referred to as pruning.
It saves time, money and CO2 and ultimately also allows a deeper search in the hyperparameter space.
The use of the SignificanceRepeatedTrainingPruner is optional and can easily be omitted.

So if you are curious now: The project is available on GitHub under [MIT license](https://opensource.org/licenses/MIT)
as part of the Deutsche Telekom open source effort: <https://github.com/telekom/census-income-lightgbm>
