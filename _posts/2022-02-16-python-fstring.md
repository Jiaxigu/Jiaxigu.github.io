---
layout: post
title: Python F-strings
tags: Programming
---

Since Python 3.6, a new feature called _formatted string literals_ or _f-strings_ has been introduced to the string fomatting arsenal. It boasts better simplicity and readability than the reigning strategy, `str.format`.

## Demo

Here is a simple example of _f-strings_:

```python
from datetime import datetime
name = 'Jiaxi'
start = datetime(2018, 10, 29)
f'Hello {name}, you have spent {(datetime.now() - start).days} days at Alibaba!'
>>> 
```

In comparison, the old `str.format` is less readable.

```python
'Hello, {}! you have spent {} days at Alibaba!'.format(
	name, (datetime.now() - start).days
)
```

There is another way to format strings, called _template strings_, that could come handy in niche situations.

```python
from string import Template
t = Template('Hello, $name! you have spent $days days at Alibaba!')
t.substitute(name=name, days=(datetime.now() - start).days)
```

This method works well ingesting user-generated tokens and strings, preventing security issues.

## References

- [https://realpython.com/python-string-formatting/]()
