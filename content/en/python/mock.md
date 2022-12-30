---
title: Mock
---

## Links
- [unittest.mock Python doc](https://docs.python.org/3/library/unittest.mock.html)
  - [`patch`](https://docs.python.org/3/library/unittest.mock.html#patch)
  - [`patch.object`](https://docs.python.org/3/library/unittest.mock.html#patch-object)
  - [`PropertyMock`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.PropertyMock)
  - [`mock_calls`](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.Mock.mock_calls)

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
mock("foo", bar="something_I_do_not_care_about")
mock.assert_called_once_with("foo", bar=ANY)
```

## Spy
If you do not want to replace a function with a mock,
but want to observe the parameters passed to the function,
a so-called spy can be used.

### Spy on a Function
To do this we use a combination of `patch` and the `wraps` argument.
Note that the first argument of `patch` is a string.

Example:
```python
def my_function(x):
    return x + 1

with patch("__main__.my_function", wraps=my_function) as wrapped_function:
    result = my_function(5)
    assert result == 6
    wrapped_function.assert_called_once_with(5)
```

### Spy on a Method
To do this we use a combination of `patch.object` and the `wraps` argument.
Note that the first argument of `patch.object` is a object (instance).

Example:
```python
class MyClass:
    def my_function(self, x):
        return x + 1

my_instance = MyClass()
with patch.object(my_instance, 'my_function', wraps=my_instance.my_function) as wrapped_method:
    result = my_instance.my_function(5)
    assert result == 6
    wrapped_method.assert_called_once_with(5)
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
