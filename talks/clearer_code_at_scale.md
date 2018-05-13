# Clearer Code at Scale

Zulip: Open Source Chat

Zulip community is robust because of reviewing and because it's fairly easy to
dive into the codebase.

## The Code is clear

Essential for reviewing

`mypy` - a way to track code clarity

Optional static typing for python

## Understanding code

```python
def big_function(...):
  ...
  thing.validate(data)
  ...
```

**It's much harder to read code than to write it**

Sometimes, `validate` is over-used (it's too good of a word)

So, what is the type of *thing*?

Often, you'll grep the call of the function.

## Easy!

```python
def big_function(..., thing: someClass, ...):
  ...
  thing.validate(data)
  ...
```

If you're still on python 2.7: static types work for you too!

Zulip moved from python 2 to 3. It made migration easy!

# Principles for moving on typing

1. Work incrementally
2. Define a clean build
3. Get started in a week
4. Let robots do the boring work

## Incrementally

* Static types are gradual: typed portion of untyped codebase still benefits
* Start with a few files/functions, add more bit-by-bit

## Define a clean build

To benefit from type annotations

* you must be able to trust them
* must regularly run a type-checker

Define a reproducible build. Run it in your CI, and locally.

Set of files - select a subset
```bash
$ tools/mypy
 tools/mypy

git ls-files zerver/ |
  grep -f tools/mypy-includes |
  grep -vf tools/mypy-excludes |
  xargs mypy

tools/mypy  # check out zulip's repo
```
https://github.com/zulip/zulip/blob/master/tools/run-mypy

Write down options `mypy.ini`

Pin the mypy version
Run it in CI

## Getting started in a week

- Check toplevel code
- Check inside functions
- `mypy.ini`

```ini
[mypy]
follow_imports=
```

1. Start with core libraries for abstractions
2. Most-called code, and newly modified code
3. Back-fill the rest

## Robots do the boring work

Worth it to write down once and for all...

### Trace at runtime

- MonkeyType (instagram / facebook)
- PyAnnotate (Dropbox)
- Several others

### infer wisely

- `pytype` (Google) will infer types

instagram runs MonkeyType in production (!):
(randomly)

```python
if random.random() < 0.00001:
```

## Expect your coworkers to love it once they see it in action
