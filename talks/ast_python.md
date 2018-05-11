# Abstract Syntax Tree (AST)


Parse Tree vs AST: Parse tree will be a 1:1 mapping of python code to tree fmt

A lot of complication in Parse tree

AST would be focusing on the semantics. You lose from information going to an AST

Parse tree: `astor`, `meta`, `codegen`

```python
import ast, dis
node = ast.parse(source, mode='exec')  # use exec vs eval (eval is only expressions)
type(node)
ast.dump(node)
compiled = compile(node, '<string>', mode='exec')
type(compiled) # <class 'code'>
```

## Code objects

Immutable data structures used as an internal representation of a piece of python code

co_name:
co_varnames: local variables
co_stacksize: computed stack size

co_code: string representing the sequence of byte code and instructions
`b'\x00d'`
`exec(compiled)`

We get back byte opcodes
To hand them, we use the `dis` module.
`dis.show_code(compiled)`

## Optimizations

Python's compiler is purposely simple

Peephole Optimizer

Very few AST optimizations besides constant folding

### Peephole

"Looking around without using your head"

folding the solutions down into variables and double negs `not not = True`

`dis.dis('not a not in b')`
`dis.dis('a in b')`

## How AST affects your code

Bytecode is created using an AST
Bytecode is stored in *.pyc files

### Example projects

- code generators
  - Hypothesis: generates tests for you (cover cases / id edge cases)
  - cog (file/text generation)
- alternative interpreters
- Transpiling
  - VOC (PyBee)
  - Transcrypt (Python to JS)
- Code transformations
  - Jinja (templating)
- Code Analysis
  - Python Security's PyT
- Code linting
- Code formatters
  - YAPF
  - Black
  - Prettier
- Code transformations
  - Post-CSS
  - Babel
  - Migrations 2 → 3
  - React Native - Native Mobile Applications from a single code base

### Practical Applications

- Improve and speed up code
- Debug errors / oddities
- Change the Python Grammar
- Round-Tripping

#### Round Tripping

Compare AST from code before and after to compare and see how they differ --
ensures that the underlying semantics of the code stays the same.


### AST Optimizations - constant folding
