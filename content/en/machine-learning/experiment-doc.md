---
title: Experiment Documentation
---

You should document what you did and why. The purpose is that you can
repeat everything later (same data, same code, same modules) and loose
no insights. The experience shows that it is tempting to do just a quick
experiment but two days later you forgot all your valuable insights.

This is a documentation template:

```
Identifier: <unique name or id to be able to reference the experiment>
Date / Period: <can also be a range for long running experiments>
Goal: <What is the goal of this experiment? What is the hypothesis? Why do we do this experiment? What do you want to show?>
Data Source: <The data you used. Source, link, filename, histogram, GIT commit id, ...>
Base Model / Model Architecture: <The base model in case of transfer learning, architecture of the model, ...>
Data Preprocessing: <Preprocessing steps, filename, histogram, GIT commit id, ...>
Code: <Which script / notebook is used? GIT commit id>
Output: <Where do you store the output, filename, GIT commit id>
Hardware: <Which and how many GPUs / CPUs / RAM - everything that could influence the results>
Modules: <which pip modules with version - GIT commit id of the requirements.txt>
Termination criterion: <how many trials do you want to train, how long do you want to try>
Results: <only the numbers>
Insights: <The interpretation of the results. What did we learn? Did we reach our goal?>
Next Steps: <Follow up experiments, ideas>
Open Questions / Ideas: <Open and unanswered questions, ideas, notes, things for later>
```
