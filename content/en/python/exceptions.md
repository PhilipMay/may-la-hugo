---
title: Exceptions
---

# Exceptions
- Built-in Exceptions: <https://docs.python.org/3/library/exceptions.html>

## Most Important Exceptions
- `TypeError`: Raised when an operation or function is applied to an
  object of inappropriate type. The associated value is a string
  giving details about the type mismatch.
- `NotImplementedError`: In user defined base classes, abstract
  methods should raise this exception when they require derived
  classes to override the method, or while the class is being
  developed to indicate that the real implementation still needs to be
  added.
- `ValueError`: Raised when an operation or function receives an
  argument that has the right type but an inappropriate value, and the
  situation is not described by a more precise exception such as
  IndexError.

## Logging Exceptions
```python
try:
    something()
except Exception:
    logger.error("something bad happened", exc_info=True)
```

also see <https://www.loggly.com/blog/exceptional-logging-of-exceptions-in-python/>
