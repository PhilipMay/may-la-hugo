---
title: Logging
---

## Links
- [Logging HOWTO](https://docs.python.org/3/howto/logging.html)
  - [Basic Logging Tutorial](https://docs.python.org/3/howto/logging.html#basic-logging-tutorial)
  - [Advanced Logging Tutorial](https://docs.python.org/3/howto/logging.html#advanced-logging-tutorial)
  - [Logging Levels](https://docs.python.org/3/howto/logging.html#logging-levels)

## Log variable Data
Logging uses the old "%-style" of string formatting.
Also see: https://docs.python.org/3/howto/logging.html#logging-variable-data

Example:
```python
logging.warning("%s before you %s', 'Look', 'leap!")
```

## Root Logger Configuration
The easiest way to configure the root logger works like this:

```python
import logging
logging.getLogger().setLevel(logging.INFO)
logging.getLogger().addHandler(logging.StreamHandler())
```
