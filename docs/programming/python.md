# Python

TODO

## Syntax

```python
# Operators

# Loops

# Lists

# Tuples

# Dictionaries

# Sets and Unions

# Iterators

# List comprehensions

# Generators

# Assertions

# Context Managers / with

# Classes / OOP

# Decorators
```

## Type Hinting

- [Python type hints: \*args and \*\*kwargs](https://adamj.eu/tech/2021/05/11/python-type-hints-args-and-kwargs/)
- [Python type hints: Use `object` instead of `Any`](https://adamj.eu/tech/2021/05/07/python-type-hints-use-object-instead-of-any/)

## Logging

Python has plenty of built-in functionality for logging via the [logging](https://docs.python.org/3/library/logging.html#module-logging) module.

## Performance and Profiling

- [Python wiki](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)
- [Python Performance Tuning: 20 Simple Tips](https://stackify.com/20-simple-python-performance-tuning-tips/)

It's always important to _measure_ the performance of your programs when trying to isolate performance issues and/or bottlenecks. Even if you think you know all the subtle optimization going on under the hood, you may have any number of misconceptions about how your programming language is actually executing instructions on the machine. _Especially_ for Python since it's backed by CPython many operations may already be executing fairly optimized implementations, but others may not be (think 3rd party dependencies). So, you can never be sure.

Understanding the context of your program and profiling will always beat your gut. Just measure, then you'll know.

There are several useful tools for profiling your Python programs. Some available in the standard library and some 3rd party tools.

| Tool | Description |
| --- | --- |
| [Scalene](https://github.com/plasma-umass/scalene) | A high-precision CPU, GPU, and memory profiler for python. Unfortunately also includes AI (LLM) recommendation, but they're optional. |

## Project Management and Virtual Environments

- [uv](https://docs.astral.sh/uv/)
- [Virtualenv](https://virtualenv.pypa.io/en/latest/)
- [Poetry](https://python-poetry.org/docs/basic-usage/)
