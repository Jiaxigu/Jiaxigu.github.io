---
layout: post
title: Python F-strings
tags: Programming
---

Since Python 3.6, a new feature called _formatted string literals_ or _f-strings_ has been introduced to the string fomatting arsenal. It boasts better simplicity and readability than the reigning strategy, `str.format`.

## Demo

Here is a simple example of _f-strings_:

```python
name = "Bryan"
weekday = "Wednesday"
normal_jobs = 10
f'Hello, {name}! Happy {weekday}! Today your have {2 * normal_jobs} to do, twice as many in a normal day!'
>>> 
```

In comparison, the old `str.format` is less readable.

```python
'Hello, {}! Happy {}! Today your have {} to do, twice as many in a normal day!'.format(
	name, weekday, 2 * normal_jobs
)
```

There is another way to format strings, called _template strings_, that could come handy in niche situations.

```python
from string import Template
t = Template('Hello, $name! Happy $weekday! Today your have $jobs to do, twice as many in a normal day!')
t.substitute(name=name, weekday=weekday, jobs=2*normal_jobs)
```

This method works well ingesting user-generated tokens and strings, preventing security issues.

## References

- [https://realpython.com/python-string-formatting/]()
