---
title: Anomalies in the MLSUM Dataset
date: 2022-02-23
tags:
  - german-data
  - mlsum
  - mt5
  - summarization
  - t5
categories:
  - NLP
---

While evaluating the [ml6team/mt5-small-german-finetune-mlsum](https://huggingface.co/ml6team/mt5-small-german-finetune-mlsum) summarization model,
my colleague [Michal Harakal](https://www.harakal.de/) and I noticed that in many cases this model for summarization simply reproduces the first
sentence of the input text.
Instead, it should generate an independent summary of the whole text.

{{< figure src="/img/posts/text-unsplash.jpg" caption="Photo by [Sandy Millar](https://unsplash.com/photos/Kl4LNdg6on4)" >}}

This extractive behavior should not happen with this model type. This is because it is an abstractive summarization model.
**Abstractive summarization** methods attempt to create a summary by interpreting the input text using NLP techniques to generate a new,
shorter text that contains the most important information from the original text.

We tried to get to the bottom of this behavior and looked at the training data set.
The data set is called [MLSUM](https://arxiv.org/abs/2004.14900).
It is available in different languages. However, we have focused on the German language.
Our analysis revealed the following:

The German training data contains 220,887 pairs of text and summary.
In 126,270 (more than half) of them the summary is completely included in the text.
This is very bad for training abstract summary models.
The model does not learn to generate a summary but to extract a sentence.
Since this sentence is usually even the first sentence, when using MLSUM one does not train a summarization model,
but a “first sentence extractor”.

This is a good example of how dangerous it is to use supervised learning data in a careless way.
Our solution was to simply remove the summary sentences from the text.
So the text can be used for training after all.

For better reproducibility, the code of this evaluation is published as a
[Colab Notebook](https://colab.research.google.com/drive/1Dayq4n9A4rT7AKkW1OP5MEMtKpYhtHS-?usp=sharing).
We have also published the resulting model called
[deutsche-telekom/mt5-small-sum-de-en-v1](https://huggingface.co/deutsche-telekom/mt5-small-sum-de-en-v1)
under open-sorce license.
