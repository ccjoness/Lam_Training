# Writing Resilient Python

## Clarity of Code
Only have one statement per line. This will ensure your code is easier to read and debug.

Bad:
```python
print("one"); print("two")
```

Good:
```python
print("one")
print("two")
```

Be descriptive with your naming conventions. In addition to commenting this will help 
create code that is easy to understand and reuse.

Bad:
```python
def x(y, z):
    return y + z
```

Good:
```python
def add_two_numbers(first_num, second_num)
    """Takes two integers or floats and adds them together"""
    return first_num + second_num
```


## Be efficient. 
Don't reinvent the wheel. Using modules that other people have created saves time and energy. Python has a large user base that creates and maintains many useful modules.

Don't repeat yourself. If you find you are writing the same code over again, create a function that you can call instead.

--- 

## Naming conventions
Naming things correctly is important. It will allow you to identify types and objects by sight.
- Classes: Uses CamelCase.
```python
class ThisClass:
    ...
```
- Functions, Variables, and arguments: Uses snake_case.
```python
def test_table_view(request_obj):
    ...

test_table = ...
```
- Constants: Uses all caps SNAKE_CASE.
```python
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
```

## Comment Code
One of the best ways to make your python code resilient is to comment everything. 
There are two ways you should comment:
Docstrings (""" or ''') are useful when describing how to use your code.
```python
"""I am an example of a docstring"""
```
Hashes (#) are useful when you need to explain what a single line of code is doing.
```python
# I am an example of an inline comment using a hash.
```

## Use the PEP 8 Guidelines (Use a code linter)
[PEP 8](https://www.python.org/dev/peps/pep-0008/) is the style guide for python. While there may be a lot of rules, it 
is a very useful tool to ensure we are writing resilient code. It's a good idea to look through the [PEP 8](https://www.python.org/dev/peps/pep-0008/) documentation. 

To help you learn to write your code to the [PEP 8](https://www.python.org/dev/peps/pep-0008/) standards you should use a python linter. After a while writing code to the standard will become second nature.

Here is a good page on setting up a python linter in vscode. https://code.visualstudio.com/docs/python/linting

## The Zen of Python (import this)
The Zen of Python, by Tim Peters

Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren't special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one-- and preferably only one --obvious way to do it.

Although that way may not be obvious at first unless you're Dutch.

Now is better than never.

Although never is often better than *right* now.

If the implementation is hard to explain, it's a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea -- let's do more of those!

