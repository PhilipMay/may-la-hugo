---
title: Iterate
---

- break `iterable` into lists of length `n`: `list(more_itertools.chunked(iterable, n))` - [see](https://more-itertools.readthedocs.io/en/stable/api.html#more_itertools.chunked)

## Dict

### Iterate keys of dict
```python
d = {'x': 1, 'y': 2, 'z': 3}
for key in d:
    print(key, 'corresponds to', d[key])
```

### Iterate keys and values of dict:
```python
d = {'x': 1, 'y': 2, 'z': 3}
for key, value in d.items():
    print(key, 'corresponds to', value)
```
