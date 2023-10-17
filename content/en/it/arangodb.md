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
#### Query all documents from a collection:
- also see [FOR (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-for.html)
```text
FOR doc IN collection
  RETURN doc
```

#### Filter documents from a collection:
- also see [FILTER (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-filter.html)
```text
FOR doc IN collection
  FILTER doc.name == "Philip"
  RETURN doc
```

#### Filter documents without `surname` attribute name from a collection:
- also see [HAS (v3.11)](https://www.arangodb.com/docs/3.11/aql/functions-document.html#has)
```text
FOR doc IN collection
  FILTER HAS(doc, "surname")
  RETURN doc
```

#### Query at most 10 documents from a collection:
- also see [LIMIT (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-limit.html)
```text
FOR doc IN collection
  LIMIT 10
  RETURN doc
```

#### Filter and count documents from a collection:
- also see [COLLECT (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-collect.html)
- also see [COLLECT WITH COUNT (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-collect.html#group-length-calculation)
```text
FOR doc IN collection
  FILTER doc.name == "Philip"
  COLLECT WITH COUNT INTO length
  RETURN length
```

#### Group and Count
- group by attribute and count
- also see [COLLECT (v3.11)](https://www.arangodb.com/docs/3.11/aql/operations-collect.html)
```text
FOR doc IN collection
  COLLECT attribute = doc.attribute WITH COUNT INTO count
  RETURN {
    "attribute" : attribute,
    "count" : count
  }
```

#### Rename Attribute
```text
FOR doc IN collection
  UPDATE doc WITH { new_name: doc.old_name } IN collection
  OPTIONS { keepNull: false }
```

#### Delete Attribute
- also see [UPDATE (v3.11)](https://www.arangodb.com/docs/stable/aql/operations-update.html#keepnull)
```text
FOR doc IN collection
  UPDATE doc WITH { not_needed: null } IN collection
  OPTIONS { keepNull: false }
```

#### Add a new Attribute
- also see [UPDATE (c3.11)](https://www.arangodb.com/docs/stable/aql/operations-update.html)
```text
FOR doc IN collection
  UPDATE doc
  WITH { new_attribute: "new_value" } 
  IN collection
```
