---
title: Python - First n items from dictionary / List
description: Extract first n items from any iterable.
tags: python
headerImage: /post/python.png
datePublished: '2020-02-28'
lastModified: '2020-02-28'
---

Fetch first\* n items from a collection using the following techniques:

## From any dictionary or list or iterable

`islice` method from `itertools` can be used to extract the given number of items from any iterable.

```python
from itertools import islice
list(islice(iterable, n))
```

\*Order is defined by iterable.

### In action

#### Fetch 3 item from a dictionary

```python
record = {'name': 'mighty', 'handler': '@DM8tyProgrammer', ...}

list(islice(record, 3))
```

#### Fetch top 5 from a list of tuples

```python
students = [("Alex", 30), ("Bob", 50"), ...]

list(islice(sorted(students, key = lambda s: s[1]), 5))
```

## From List

If the type of collections is known to be `list` , then square bracket can also be convenient.

```python
numbers = [1, 2, 4, 5]
print(numbers[:2])
```
