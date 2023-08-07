---
title: Logging
---

## Links
- [Logging HOWTO](https://docs.python.org/3/howto/logging.html)
  - [Basic Logging Tutorial](https://docs.python.org/3/howto/logging.html#basic-logging-tutorial)
  - [Advanced Logging Tutorial](https://docs.python.org/3/howto/logging.html#advanced-logging-tutorial)
  - [Logging Levels](https://docs.python.org/3/howto/logging.html#logging-levels)

## Module-Level Logger
A convention is to use a module-level logger as follows:
```python
import logging
_logger = logging.getLogger(__name__)
```

## Log variable Data
Logging uses the old "%-style" of string formatting.
Also see:
- [Logging variable data](https://docs.python.org/3/howto/logging.html#logging-variable-data)
- [Old string formatting](https://docs.python.org/3/tutorial/inputoutput.html#old-string-formatting)
- [`printf`-style String Formatting](https://docs.python.org/3/library/stdtypes.html#old-string-formatting)

Example:
```python
_logger.warning("%s before you %s', 'Look', 'leap!")
```

## Root Logger Configuration
The easiest way to configure the root logger works like this:

```python
import logging
logging.basicConfig(format="%(levelname)s:%(message)s", level=logging.DEBUG)
```

## Change Logger Level
Example:
```python
logging.getLogger("module").setLevel(logging.DEBUG)
```
