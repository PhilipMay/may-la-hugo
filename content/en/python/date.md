---
title: Date & Time
---

## Links
- [datetime - Basic date and time types](https://docs.python.org/3/library/datetime.html)
  - [datetime.isoformat - convert to ISO 8601](https://docs.python.org/3/library/datetime.html#datetime.datetime.isoformat)
  - [datetime.astimezone - convert timezone](https://docs.python.org/3/library/datetime.html#datetime.datetime.astimezone)
  - [datetime.strptime - parse string to `datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime.strptime)

## Examples

### Now, ISO 8601 and UTC
#### Current date and time in ISO 8601 format:
```python
from datetime import datetime
date = datetime.now().isoformat()
print(date)
# output example: 2023-07-08T07:13:01.359471
```

#### Current date and time in ISO 8601 format in seconds resolution:
```python
from datetime import datetime
date = datetime.now().isoformat(timespec="seconds")
print(date)
# output example: 2023-07-08T07:13:44
```

#### Current date and time in ISO 8601 format normalized to UTC time:
```python
from datetime import datetime
date = datetime.now().astimezone().isoformat()
print(date)
# output example: 2023-07-08T07:14:41.370299+02:00
```

#### Current date and time in ISO 8601 format normalized to UTC time in seconds resolution:
```python
from datetime import datetime
date = datetime.now().astimezone().isoformat(timespec="seconds")
print(date)
# output example: 2023-07-08T07:17:02+02:00
```

### Parsing
#### Parse date string (no time) to ISO 8601 format:
```python
from datetime import datetime
date = datetime.strptime("04.01.1976", "%d.%m.%Y").date().isoformat()
print(date)
# output example: 1976-01-04
```
