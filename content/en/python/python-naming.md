---
title: Python Naming
---

This is about how things are named in Python.

## Classes

- class object: the raw class itself (not instantiated)
([see here](https://docs.python.org/3/tutorial/classes.html#class-objects))
- instance object or instance of a class: an instantiated class like `x = MyClass()`
([see here](https://docs.python.org/3/tutorial/classes.html#class-objects))\
an instance object has two kinds of valid attribute names:
  - data attributes: are variables belonging to the instance,
  attributes need not be declared - like local variables - they spring into existence when they are first assigned to
  - methods: method is a function that “belongs to” an object
- class variables: for attributes (and methods) shared by all instances of a class
([see here](https://docs.python.org/3/tutorial/classes.html#class-and-instance-variables))
- instance variables: for data unique to each instance
([see here](https://docs.python.org/3/tutorial/classes.html#class-and-instance-variables))

### classmethod
see https://www.geeksforgeeks.org/class-method-vs-static-method-python/

### staticmethod
see https://www.geeksforgeeks.org/class-method-vs-static-method-python/

### constructor vs. initializer vs. allocator (`__init__`)
see https://stackoverflow.com/a/6578504
