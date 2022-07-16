---
title: Typing
---

## Links
- https://docs.python.org/3/library/typing.html

## Types
- `Any`: Special type indicating an unconstrained type.
- `Optional`: Optional type.
- `Dict`
  - `Dict[str, int]`
  - `Dict[str, List[int]]`
- `Callable`
  - `Callable[[str], Dict[str, List[int]]]`

## Example

```python
    def __init__(
        self,
        tokenizer_func: Callable[[str], Dict[str, List[int]]],
        augmentation_func: Callable[[str], str],
        train_data_sampling_callback: Callable[[List[str]], List[int]] = None,
    ):
```
