---
title: Optuna
---

## Links
  - Add additional hyperparameter to existing study (workaround)
      - <https://github.com/optuna/optuna/issues/1855>
      - <https://colab.research.google.com/drive/1KiqPqJZ5JL6pOZsNvrQ63KQk9BV65voG#scrollTo=Ck-G9eh4W33n>

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

## Extend HP-space
It might be that the HP space was selected to narrow and we want to extend it during a study to continue the HP search with an extended HP space. This is a bit difficult in Optuna.

This is known to the Optuna maintainers but needs someone to write a pull request. Details here: https://github.com/optuna/optuna/issues/4037

A workaround is as following:

Lets say we had a hyperparameterspace with num_epochs from 2 to 4. Now we did some trials for this study but want to extend num_epochs to 2 to 7. This is done like this:

```python
# load old study
study_name = "my_study_01"
storage='sqlite:///optuna.db'
study = optuna.create_study(
    study_name=study_name,
    storage=storage,
    load_if_exists=True,
    direction='maximize',
)

# iterate trials from old study and modify (extend) the distributions
new_trials = []
for trial in study.trials:
    # this is only valid for int distributions
    # if it is a float distribution this needs to be changed
    trial.distributions["num_epochs"] = optuna.distributions.IntDistribution(2, 7)

    new_trials.append(trial)

# delete old study from memory
# for some reason I always do this because there was some trouble in the past
# but I do not remember why - maybe because there is a DB connection behind it
del study

# create new study
study_name_new = "my_study_02"
new_study = optuna.create_study(
    study_name=study_name_new,
    storage=storage,
    load_if_exists=True,
    direction='maximize',
)

# add old trials to new trial
for trial in new_trials:
    new_study.add_trial(trial)

# now also modify your training code
# this would be the following change for example
# change from
# num_epochs = trial.suggest_int("num_epochs", 2, 4)
# to
# num_epochs = trial.suggest_int("num_epochs", 2, 7)

# now you can continue training on "study_name_new" with the old knowledge but extended HP space
```

## More Topics / To-do
- choose HP space
- monitor HP space / slice plot
- monitor training
- only train for x non failed iteration
- xval vs. not xval
