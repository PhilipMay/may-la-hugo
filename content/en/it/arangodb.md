---
title: ArangoDB
---

## Links
- [Manual](https://www.arangodb.com/docs/stable/)
- [ArangoDB Query Language (AQL)](https://www.arangodb.com/docs/stable/aql/)
  - [Date functions (v3.11)](https://www.arangodb.com/docs/3.11/aql/functions-date.html)
- [Python-Arango @ GitHub](https://github.com/ArangoDB-Community/python-arango)
- [Python-Arango doc](https://docs.python-arango.com/en/main/)

## AQL Examples
Query all documents from a collection:
```text
FOR doc IN collection
  RETURN doc
```

Filter documents from a collection:
```text
FOR doc IN collection
  FILTER doc.name == "Philip"
  RETURN doc
```

Query at most 10 documents from a collection:
```text
FOR doc IN collection
  LIMIT 10
  RETURN doc
```

Filter and count documents from a collection:
```text
FOR doc IN collection
  FILTER doc.name == "Philip"
  COLLECT WITH COUNT INTO length
  RETURN length
```
