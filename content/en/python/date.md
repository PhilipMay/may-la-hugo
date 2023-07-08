---
title: Date & Time
---

## Links
- [datetime - Basic date and time types](https://docs.python.org/3/library/datetime.html)
  - [datetime.isoformat](https://docs.python.org/3/library/datetime.html#datetime.datetime.isoformat)
  - [datetime.astimezone](https://docs.python.org/3/library/datetime.html#datetime.datetime.astimezone)

## Examples
The current time in ISO 8601 format.
```python
from datetime import datetime
date = datetime.now().isoformat()
print(date)
# output example: 2023-07-08T07:13:01.359471
```

The current time in ISO 8601 format in seconds resolution.
```python
from datetime import datetime
date = datetime.now().isoformat(timespec="seconds")
print(date)
# output example: 2023-07-08T07:13:44
```

The current time in ISO 8601 format normalized to UTC time.
```python
from datetime import datetime
date = datetime.now().astimezone().isoformat()
print(date)
# output example: 2023-07-08T07:14:41.370299+02:00
```

The current time in ISO 8601 format normalized to UTC time in seconds resolution.
```python
from datetime import datetime
date = datetime.now().astimezone().isoformat(timespec="seconds")
print(date)
# output example: 2023-07-08T07:17:02+02:00
```
