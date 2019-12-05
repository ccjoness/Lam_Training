While the Python 3 core code is very secure, you may write things in a way that is not. Here are some tips to ensure that your code is secure.

## Use Python 3
The best argument to use Python3 is Python 2 will reach end of life in January 2020. After that it will not receive security updates. Any third party modules that rely on python 2 will also no longer be secure.

## Scan your code with a security scanner
There are many different security scanners out there. The tool I recommend is [Bandit](https://github.com/PyCQA/bandit). 

*"Bandit is a tool designed to find common security issues in Python code. To do this Bandit processes each file, builds an AST from it, and runs appropriate plugins against the AST nodes. Once Bandit has finished scanning all the files it generates a report."* 


## Be careful when downloading packages
The Python Package Index (PyPI) is going to be the typical place that you get your third party modules (via pip install). Modules added to PyPI do not get scanned for malicious code or security vulnerabilities. If a user finds any issues with a module they can report it and it will be dealt with. Most packages on PyPI are fine but you must do research on any module before you install it.

I find that open large open source modules are the best. You can see what other users are saying about them and the code is open to the public to review.

## Handle user input carefully
User input is often necessary but can create a security vulnerability if not handled correctly. When writing code that uses user input, be explicit in what actions that user can initiate.

Never let a user enter commands that will be evaluated by python code.

Bad:
```python
prompt = input('What code would you like to run?: ')
exec(prompt)
```
This would allow a user to run any python code!

If you need to let a user execute code, give them options instead.

Better:
```python
def function_1():
    print('function_1')

def function_2():
    print('function_2')

options = {'function_1': function_1, 'function_2': function_2}

prompt = input("Enter the name of the function you would like to execute: ")

try:
    options['function_1']()
except KeyError:
    print('Error: function name does not exist')
```
