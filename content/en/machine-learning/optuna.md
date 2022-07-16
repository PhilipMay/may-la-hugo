---
title: Optuna
---

## Transfer Trials to other DB
``` python
local_study = optuna.load_study(study_name="foo", storage="SQLITE URL")
remote_study = optuna.create_study(study_name="foo", storage="REMOTE SQL DB URL")

for trial in local_study.trials:
    remote_study.add_trial(trial)
```

## Save Plot to Disk
``` python
fig = optuna.visualization.plot_slice(study)
fig.write_image("<filename>.png")  # save to image
fig.write_html("<filename>.html")  # save to html
```

## How-to Links
  - Add additional hyperparameter to existing study (workaround)
      - <https://github.com/optuna/optuna/issues/1855>
      - <https://colab.research.google.com/drive/1KiqPqJZ5JL6pOZsNvrQ63KQk9BV65voG#scrollTo=Ck-G9eh4W33n>
