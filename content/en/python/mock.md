---
title: Mock
---

## Links
- [unittest.mock Python doc](https://docs.python.org/3/library/unittest.mock.html)

## Asserts
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
