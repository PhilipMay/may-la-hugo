---
title: Mock
---

## Links
- [unittest.mock Python doc](https://docs.python.org/3/library/unittest.mock.html)

## Asserts

### Assert Methods
- [`assert_called()`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_called)
- [`assert_called_once()`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_called_once)
- [`assert_called_with(*args, **kwargs)`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_called_with) -
  only passes if the call is the most recent one
- [`assert_called_once_with(*args, **kwargs)`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_called_once_with) -
  passes if the mock was called exactly once with the specified arguments
- [`assert_any_call(*args, **kwargs)`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_any_call) -
  passes if the mock has ever been called with the specified arguments
- [`assert_has_calls(calls, any_order=False)`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_has_calls)
- [`assert_not_called()`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.assert_not_called)

### Assert only some Arguments
Assert not all exact arguments but just *some* of them.

Example:
```python
from unittest.mock import Mock, ANY
mock = Mock(return_value=None)
mock("foo", bar=object())
mock.assert_called_once_with("foo", bar=ANY)
```

## Seal a Mock
Seal disables the automatic creation of mocks when accessing an attribute of the mock.
Also see: https://docs.python.org/3/library/unittest.mock.html#unittest.mock.seal

One problem with normal mocks is that they auto-create attributes on demand.
If you misspell one of these assert methods then your assertion is simply swallowed and ignored.
If you seal the mock after creation this avoids this problem.

Example:
```python
from unittest.mock import Mock, seal
mock = Mock()
# more configuration here
seal(mock)
```
