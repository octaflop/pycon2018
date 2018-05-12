# Elegant Solutions for Python problems
## Nina Zakharenko

http://bit.ly/elegant-python-2018

# Zen

`import this`


# Magic Methods

dunder ~= `__`

Make your objects behave like different builtins

Eg, Numbers, lists, dicts

```python
class Money:
  currency_rates = {
    '$': 1,
    'Ē': eg
  }

  def __add__(self, other):
    #

>>> print(obj + obj2)
```

## Some magic methods map to symbols

`d.__get__item('thing')`

## Some magic methods map to built-in functions

# Custom Generators

Makes classes iterable
Just implement: `__iter__()`

Implement `__next__()` → must raise exception `raise StopIteration` when done.

## When you don't need to maintain state: use a generator instead

Return → `yield`

# Method Magic

```python
>>> # alias
>>> Word.__add__ = Word.concat
```

```python
getattr(dog_instance, 'string_of_method', 'default return')
```

# `agithub`

A REST API client with a syntax which facilitates rapid prototyping on any API

# Feature Flags


Context management via classmethods

We use `__enter__` and `__exit__` we turn something on and off

built

You can add a context manager

# ContextDecorator

Use as a decorator OR a context manager

! Read Source code more often
