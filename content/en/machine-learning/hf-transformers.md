---
title: Hugging Face - Transformers
---

## Links
- [Transformers Doc](https://huggingface.co/transformers/) - [Examples](https://huggingface.co/transformers/examples.html)
- [Transformers GitHub](https://github.com/huggingface/transformers)
- [Messageboard](https://discuss.huggingface.co/categories)
- HF @ Medium: <https://medium.com/huggingface>
- Model sharing and uploading:
  <https://huggingface.co/transformers/model_sharing.html>

## Model
- `transformers.AutoConfig` -
  [doc](https://huggingface.co/transformers/model_doc/auto.html#autoconfig) -
  [impl](https://github.com/huggingface/transformers/blob/master/src/transformers/configuration_auto.py)
- Save a pretrained model:
  <https://huggingface.co/transformers/main_classes/model.html?highlight=save_pretrained#transformers.PreTrainedModel.save_pretrained>

## Training
- `transformers.TrainingArguments` -
  [doc](https://huggingface.co/transformers/main_classes/trainer.html#trainingarguments)
- `transformers.Trainer` -
  [doc](https://huggingface.co/transformers/main_classes/trainer.html) -
  [impl](https://github.com/huggingface/transformers/blob/master/src/transformers/trainer.py)
- Metrics (scroll down):
  <https://huggingface.co/transformers/training.html#trainer>
- Learning Rate Schedules:
  <https://huggingface.co/transformers/main_classes/optimizer_schedules.html?highlight=warm%20restart#learning-rate-schedules-pytorch>
- Freezing the encoder:
  <https://huggingface.co/transformers/training.html?highlight=freezing#freezing-the-encoder>
- Early Stopping
  - [PR](https://github.com/huggingface/transformers/pull/4186)
  - <https://github.com/huggingface/transformers/pull/7431>
- Custom Loss Function to add class weights for unbalanced datasets:
  Subclass `Trainer` and override the `compute_loss` method (see
  example
  [here](https://huggingface.co/transformers/master/main_classes/trainer.html)).
- Multi Class (multi head) classification:
  <https://discuss.huggingface.co/t/how-do-i-do-multi-class-multi-head-classification/1140>

## Tokenizer
- `tokenizers.BertWordPieceTokenizer` - for vocab generation -
  [impl](https://github.com/huggingface/tokenizers/blob/master/bindings/python/py_src/tokenizers/implementations/bert_wordpiece.py)
- `tokenizers.normalizers.BertNormalizer` -
  [impl](https://github.com/huggingface/tokenizers/blob/master/bindings/python/py_src/tokenizers/normalizers/__init__.pyi)
- `transformers.tokenization_bert.BertTokenizer` - tokenizer for
  normal usage -
  [impl](https://github.com/huggingface/transformers/blob/master/src/transformers/tokenization_bert.py)
- `transformers.tokenization_bert.BertTokenizerFast` - fast tokenizer
  for normal usage -
  [impl](https://github.com/huggingface/transformers/blob/master/src/transformers/tokenization_bert.py)
- `tokenizers.AutoTokenizer` -
  [doc](https://huggingface.co/transformers/model_doc/auto.html#autotokenizer) -
  [impl](https://github.com/huggingface/transformers/blob/master/src/transformers/tokenization_auto.py)
- `PreTrainedTokenizerBase.__call__` -
  [doc](https://huggingface.co/transformers/internal/tokenization_utils.html#transformers.tokenization_utils_base.PreTrainedTokenizerBase.__call__)

## Pipelines
- GitHub:
  <https://github.com/huggingface/transformers/blob/master/src/transformers/pipelines.py>
- `TextClassificationPipeline` -\> `Pipeline` -\> `_ScikitCompat`

## Data Handling
- <https://github.com/huggingface/nlp>
- Usage Example:
  <https://colab.research.google.com/drive/1-JIJlao4dI-Ilww_NnTc0rxtp-ymgDgM>
- Fine-tuning with custom datasets:
  <https://huggingface.co/transformers/master/custom_datasets.html#fine-tuning-with-custom-datasets>

## Important Torch Classes
- [DataLoader](https://pytorch.org/docs/stable/data.html#torch.utils.data.DataLoader)

## Links & Know-how
- <https://jalammar.github.io/illustrated-transformer/>
- <https://www.youtube.com/watch?v=PNNHaQUQqW8>
- <https://github.com/huggingface/naacl_transfer_learning_tutorial>
- <https://ruder.io/thesis/>
