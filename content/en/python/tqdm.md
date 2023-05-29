---
title: tqdm
---

## Links
- s<https://github.com/tqdm/tqdm>

## Usage
Simple usage:
```python
from tqdm import tqdm

for i in tqdm(range(10000)):
    # ...
```

Manual usage:
```python
from tqdm import tqdm

with tqdm(total=100) as pbar:
    for i in range(10):
        sleep(0.1)
        pbar.update(10)
```

- automatically choose between console or notebook versions: `from tqdm.auto import tqdm`
