# Advanced Python
Advanced Python tips and tricks. This includes methods in optimising and improving the speed of your Python code.

### Keyword and Positional-only arguments
You can separate the positional arguments with keyword-only arguments with an '*'. This is to improve code readability.

```
def fab(arg1, arg2, *, arg3=False):
    return 'fab'
```

Similarly you can positonal-only arguments with a `/` character. Python 3.8+

```
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
```

## Classes and objects

### [Data classes](https://docs.python.org/3/library/dataclasses.html)
Available from Python3.7

```
from dataclasses import dataclass

@dataclass
class InventoryItem:
    """Class for keeping track of an item in inventory."""
    name: str
    unit_price: float
    quantity_on_hand: int = 0

    def total_cost(self) -> float:
        return self.unit_price * self.quantity_on_hand
```
You can make a dataclass instance immutable by passing `frozen=True` to the decorator. However, there is a performance cost to this.

### [__slots__](https://docs.python.org/3/reference/datamodel.html#slots)
Explicitly declare data members and deny the creation of `__dict__` and `__wakeref__` in order to give you a performance boost (e.g. saving memory, and faster attribute access). More detailed explanation and usage can be found [here](https://stackoverflow.com/questions/472000/usage-of-slots). `__slots__` is a feature of `dataclass` as of Python 3.10.

```
class Base:
    __slots__ = 'foo', 'bar'
```

### Computed attributes
Computing based on an objects set of attributes might be useful in various scenarios.

This example uses the `__getattr__` to compute some value based on the objects attributes.
```
class Point:
  def __init__(self):
      self.x = 23
      self.y = 87
  
  def __getattr__(self, attr):
      if attr == "vec":
          return (self.x, self.y)
```

* TODO: `__setattr__`

### Class numerical operators
You can add an `i` to each of the keywords below in order to allow for the respective shorthand operation. e.g. `self += other`.

* `__add__`
* `__sub__`
* `__mul__`
* `__div__`
* `__floordiv__`
* `__pow__`
* `__and__`
* `__or__`


## Other

### Template strings

```
from string import Template

t = Template("Hello ${name}")
str1 = t.substitute(name="Bob")
```

* Variable argument list.
* Logging

# Faster Python
## Profiling
### line_profiler
line_profiler is a module for doing line-by-line profiling of functions. kernprof is a convenient script for running either line_profiler or the Python standard library's cProfile or profile modules, depending on what is available.

`line_profiler` is an external package that can be installed by `pip install line_profiler`.

* In order to a profile a specific function, you add a decorator, `@profile`, to the desired function.
* Run `kernprof -l YOURCODE.PY`, this will create a *.lprof file for you which can be viewed by running `python3 -m line_profiler YOURCODE.PY.lprof`

## Other and caching

* TODO: Measuring time
* TODO: CPU profiling
* TODO: Tracing memory allocations and memory_profiler
* TODO: Local caching of names
* TODO: Pre-calculating
* TODO: lru_cache
* TODO: Cython
* TODO: Threads and processes

# New features
These are new(ish) features that one should be aware of in order to move on to a more current way of writing python codes.

* [py3.8] **Walrus Operator:**  ':=' allows one to declare and assign a variable. `if (n := len(a)) > 10:`
* etc.

# Development environment
TODO: Common environments for productivity.

### Resources
* https://uwpce-pythoncert.github.io/SystemDevelopment/profiling.html
* [Book] Serious Python by Julien Danjou

