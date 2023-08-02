# DotDict
A simple Python library that builds upon `argparse.Namespace` to make chained attributes possible.

## Why?
Configs of all kinds follow a dict-like structure. 
However, nobody likes the `dict[key]` syntax. We all much prefer the `dict.key` syntax.

There are a number of workarounds for this, including `defaultdict` or `argparse.Namespace` (upon which this library is based).

The downside of these libraries, though, is that when you want to start a new level, you must explicitly define it first. For example:
``` python
config = defaultdict()

config.host = 'localhost'

config.users = defaultdict()
config.users.foo = 'bar'
```

This is *ugly*.

Wouldn't you much prefer the following syntax?
``` python
config = dd()

config.host = 'localhost'
config.users.foo = 'bar'
```

## Installation
Installation is simple: From this directory, run `pip install .`

## Usage
Usage is equally as simple:
```python
from DotDict import DotDict as dd

x = dd()

x.a.b.c = 1
x.a.d = 2
x.a.b.e = 3

print(x) # DotDict(a=DotDict(b=DotDict(c=1, e=3), d=2))
print(vars(x)) # {'a': DotDict(b=DotDict(c=1, e=3), d=2)}
print(vars(x.a)) # {'b': DotDict(c=1, e=3), 'd': 2}
```
