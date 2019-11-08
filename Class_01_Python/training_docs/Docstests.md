### Doctests

[Doctests](https://docs.python.org/3/library/doctest.html) are a way to embed tests inside the docstring of your module.

```python
"""
a simple module with a single method

>>> add(5,2)
7
>>> add(-1, 3)
2
>>> add(-1, -4)
-5
"""

def add(a, b):
    return a + b
```

You can then run the doctest of this module by executing `python -m doctest -v example.py`. This runs the doctest module `example.py` as an argument. If a doctest is successful, it prints nothing. If a test fails, it'll tell you the expected value and the value it received.

Instead of running the doctest on the command-line, you can have the module run the doctest directly. That way, the doctest is executed whenever the module is run.

```python
"""
>>> add(5,2)
7
>>> add(-1, 3)
2
>>> add(-1, -4)
-5
"""

def add(a, b):
    return a + b

if __name__ == "__main__":
    import doctest
    doctest.testmod()
```