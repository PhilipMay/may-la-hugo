---
title: Joblib
---

# Joblib
- <https://joblib.readthedocs.io/>

## Commands
- pickle compressed data to disk
  - `joblib.dump(data, '<the_file>.pkl.gz', compress=('gzip', 3))`
  - also see <https://joblib.readthedocs.io/en/latest/generated/joblib.dump.html>
- read compressed pickled data from disk
  - `data = joblib.load('<the_file>.pkl.gz')`
  - also see <https://joblib.readthedocs.io/en/latest/generated/joblib.load.html>
