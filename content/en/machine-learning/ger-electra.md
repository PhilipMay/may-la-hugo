---
title: German Electra Training
---

## Steps for training

### Step 1 - generate Vocab
```python
import os
from tokenizers import BertWordPieceTokenizer
from pathlib import Path

save_dir = "./<vocab_save_dir>"
paths = [str(x) for x in Path("<text_corpus_dir>").glob("*.txt")]
print('text corpus files:', paths)
vocab_size = 32_767  # 2^15-1
min_frequency = 2

os.makedirs(save_dir, exist_ok=True)

special_tokens = [
    "[PAD]",
    "[UNK]",
    "[CLS]",
    "[SEP]",
    "[MASK]"]

for i in range(767-5):
    special_tokens.append('[unused{}]'.format(i))

tokenizer = BertWordPieceTokenizer(strip_accents=False)
tokenizer.train(files=paths,
                vocab_size=vocab_size,
                min_frequency=min_frequency,
                special_tokens=special_tokens,
                )

tokenizer.save_model(save_dir)
tokenizer.save(save_dir + "/tokenizer.json")
```

### Step 2 - get modified code to disable `strip_accents`
Use the modified fork to disable `strip_accents`. Also see:
<https://github.com/PhilipMay/electra/tree/no_strip_accents> and this
PR: <https://github.com/google-research/electra/pull/88>

```bash
git clone -b no_strip_accents https://github.com/PhilipMay/electra.git
cd electra
```

### Step 3 - create TF datasets
```bash
python3 build_pretraining_dataset.py --corpus-dir ~/data/nlp/corpus/ready/ --vocab-file ~/dev/git/german-transformer-training/src/vocab_no_strip_accents/vocab.txt --output-dir ./tf_data --max-seq-length 512 --num-processes 8 --do-lower-case --no-strip-accents
```

### Step 4 - training
This needs to be done on a strong GPU or even better TPU machine.

```bash
python3 run_pretraining.py --data-dir gs://<dir> --model-name 02_Electra_Checkpoints_32k_766k_Combined --hparams '{"pretrain_tfrecords": "gs://<dir>/*" , "model_size": "base", "vocab_file": "gs://<dir>/german_electra_uncased_no_strip_accents_vocab.txt", "num_train_steps": 766000, "max_seq_length": 512, "learning_rate": 2e-4, "embedding_size" : 768, "generator_hidden_size": 0.33333, "vocab_size": 32767, "keep_checkpoint_max": 0, "save_checkpoints_steps": 5000, "train_batch_size": 256, "use_tpu": true, "num_tpu_cores": 8, "tpu_name": "electrav5"}'
```

```text
    Config:
    debug False
    disallow_correct False
    disc_weight 50.0
    do_eval False
    do_lower_case True
    do_train True
    electra_objective True
    embedding_size 768
    eval_batch_size 128
    gcp_project None
    gen_weight 1.0
    generator_hidden_size 0.33333
    generator_layers 1.0
    iterations_per_loop 200
    keep_checkpoint_max 0
    learning_rate 0.0002
    lr_decay_power 1.0
    mask_prob 0.15
    max_predictions_per_seq 79
    max_seq_length 512
    model_dir gs://<dir>
    model_hparam_overrides {}
    model_name 02_Electra_Checkpoints_32k_766k_Combined
    model_size base
    num_eval_steps 100
    num_tpu_cores 8
    num_train_steps 766000
    num_warmup_steps 10000
    pretrain_tfrecords gs://<dir>/*
    results_pkl gs://<dir>/results/unsup_results.pkl
    results_txt gs://<dir>/results/unsup_results.txt
    save_checkpoints_steps 5000
    temperature 1.0
    tpu_job_name None
    tpu_name electrav5
    tpu_zone None
    train_batch_size 256
    uniform_generator False
    untied_generator True
    untied_generator_embeddings False
    use_tpu True
    vocab_file gs://<dir>/german_electra_uncased_no_strip_accents_vocab.txt
    vocab_size 32767
    weight_decay_rate 0.01
```

### Convert Model to PyTorch
```bash
 python /home/phmay/miniconda3/envs/farm-git/lib/python3.7/site-packages/transformers/convert_electra_original_tf_checkpoint_to_pytorch.py --tf_checkpoint_path ./model.ckpt-40000 --config_file ./config.json --pytorch_dump_path ./pytorch_model.bin --discriminator_or_generator='discriminator'
```

More info on conversion:
- <https://github.com/huggingface/transformers/blob/d5d7d886128732091e92afff7fcb3e094c71a7ec/src/transformers/convert_electra_original_tf_checkpoint_to_pytorch.py>
- <https://gist.github.com/Phil1108/7fc35be4a986d751ab3ce2f6dbd6efd8>
