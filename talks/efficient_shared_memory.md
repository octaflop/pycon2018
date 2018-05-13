# Efficient Shared Memory Data Structures
## Claudio Freire

Sharing Memory: what for?

Cache too big to fit in RAM

Serialization cost becomes prohibitive

# Transition to "Shared buffer"

Read-only for stuff that doesn't change

R/W layer with continuous (infrequent) updates

## Why not multiprocessing?

Poor support for complex data types

# Best of Both Worlds

memcached for new (buffer), dynamic structure for the rest


HOW? `mmap` files

as simple as

```python
fileobj = open("buf", "r+")
buf = mmpap.mmap(
    fileobj.fileno(), 0,
    access = mmap.ACCESS_READ)
```

the trick to get objects into the map is a bit more complex

The trick: `struct`

`proxies` to make it pythonic

```python
import struct
struct.pack("if?", 1, 2.0, True)
```

```C
struct {
  int a;
  float b;
  bool c;
}
```

## Why Compare with C?

`Cython`?

Native machine, widelt portable


A proxy:

```python
x = Proxy(buf, offset=10)

x.a # reads the int
x.b # reads the float
x.c # reads the bool
```

No Serialization required

## How

Python Proxies

```C
struct ComplexProxy = {
  int value;
  int child_left_offset;
  int child_right_offset;
}
```

```python
class ComplexObj:
    def __init__(self, l=None, r=None):
        self.value = 3
        self.left = l
        self.right = r
```

# Caveat: cyclic references — OOPS!

Options: forbid them, allow them

Solve:

Identity maps: `id(object) → offset`


The thing is: we want to manipulate without serialization

# Manipulation without serialization

Structure of an object

`http://poshmodule.sourceforge.net/posh/posh.pdf`
