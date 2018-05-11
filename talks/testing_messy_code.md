# `mrname`

## Why not: arguments for

- Why shouldn't we write test for messy tests:
  - it will be replaced eventually (no, it won't)

- It's has been working just fine...
  - Has it?
  - Do you want to be the one who breaks it

- I don't have time
  - It takes more time and money to debug in the wild
  - it will take less time to add to the code in the future

- I'm lazy
  - LAZY means to lazy to fight fires

- Why Me?
  - um, there's no real answer to that

## Jumping in

Where to even start?

### Test What you Touch

Write a test that asserts a behavior before you even touch the code
Write a test for what changes

## The first test is *always* the hardest test

Before you write the first test, you need to setup

### Tools

- Test runner
- User pre-existing tools for your framework / modules
- Create scaffolding

### Examples

- `pytest` runner
- `pytest-django` runner for django
- `pytest-socket` disables socket just in case
- `pytest-cov` code coverage
- `factory_boy` for boilerplace
- `.in` file(?)


## Code example

- Start with unit tests: fast, no db (typically), no file io (typically)
- `rest_framework.APITestCase`

- `pycov` will output coverage for tests
