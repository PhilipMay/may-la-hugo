---
title: Backoff
---

[Backoff](https://github.com/litl/backoff) is a module to wrap functions such that
they will be retried until some condition is met.

## Install
```bash
pip install backoff
```

## Examples
Catch `Exception` then rety 4 times. First retry wait 5 sec., 2nd 10 sec., 3rd 20 sec. and 4th 40 sec.
Do not jitter the wait time.
```python
import backoff
@backoff.on_exception(backoff.expo, Exception, max_tries=4, factor=5, jitter=None)
def do_something():
    pass
```

Catch `Exception` then rety 4 times. Always wait 10 sec. between retry.
Do not jitter the wait time.
```python
import backoff
@backoff.on_exception(backoff.constant, Exception, max_tries=4, interval=10, jitter=None)
def do_something():
    pass
```
