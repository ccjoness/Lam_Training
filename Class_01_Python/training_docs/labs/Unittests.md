# Unittest Basic Example
The unittest module provides a rich set of tools for constructing and running tests. This section demonstrates that a small subset of the tools suffice to meet the needs of most users.

Here is a short script to test three string methods:

```python
import unittest

class TestStringMethods(unittest.TestCase):

    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())
        self.assertFalse('Foo'.isupper())

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):
            s.split(2)

if __name__ == '__main__':
    unittest.main()
```

## Command-Line Interface
The unittest module can be used from the command line to run tests from modules, classes or even individual test methods:

```
python -m unittest test_module1 test_module2
python -m unittest test_module.TestClass
python -m unittest test_module.TestClass.test_method
```
You can pass in a list with any combination of module names, and fully qualified class or method names.

Test modules can be specified by file path as well:
```
python -m unittest tests/test_something.py
```
This allows you to use the shell filename completion to specify the test module. The file specified must still be importable as a module. The path is converted to a module name by removing the ‘.py’ and converting path separators into ‘.’. If you want to execute a test file that isn’t importable as a module you should execute the file directly instead.

You can run tests with more detail (higher verbosity) by passing in the -v flag:
```
python -m unittest -v test_module
```
When executed without arguments Test Discovery is started:
```
python -m unittest
```
For a list of all the command-line options:
```
python -m unittest -h
```
## List of assert methods.
The TestCase class provides several assert methods to check for and report failures. The following table lists the most commonly used methods (see the tables below for more assert methods):

| Method                    | Checks that          | New in |
|---------------------------|----------------------|--------|
| assertEqual(a, b)         | a == b               |        |
| assertNotEqual(a, b)      | a != b               |        |
| assertTrue(x)             | bool(x) is True      |        |
| assertFalse(x)            | bool(x) is False     |        |
| assertIs(a, b)            | a is b               | 3.1    |
| assertIsNot(a, b)         | a is not b           | 3.1    |
| assertIsNone(x)           | x is None            | 3.1    |
| assertIsNotNone(x)        | x is not None        | 3.1    |
| assertIn(a, b)            | a in b               | 3.1    |
| assertNotIn(a, b)         | a not in b           | 3.1    |
| assertIsInstance(a, b)    | isinstance(a, b)     | 3.2    |
| assertNotIsInstance(a, b) | not isinstance(a, b) | 3.2    |

It is also possible to check the production of exceptions, warnings, and log messages using the following methods:

| Method                                        | Checks that                                                    | New in |
|-----------------------------------------------|----------------------------------------------------------------|--------|
| assertRaises(exc, fun, *args, **kwds)         | fun(*args, **kwds) raises exc                                  |        |
| assertRaisesRegex(exc, r, fun, *args, **kwds) | fun(*args, **kwds) raises exc and the message matches regex r  | 3.1    |
| assertWarns(warn, fun, *args, **kwds)         | fun(*args, **kwds) raises warn                                 | 3.2    |
| assertWarnsRegex(warn, r, fun, *args, **kwds) | fun(*args, **kwds) raises warn and the message matches regex r | 3.2    |
| assertLogs(logger, level)                     | The with block logs on logger with minimum level               | 3.4    |


There are also other methods used to perform more specific checks, such as:

| Method                     | Checks that                                                                   | New in |
|----------------------------|-------------------------------------------------------------------------------|--------|
| assertAlmostEqual(a, b)    | round(a-b, 7) == 0                                                            |        |
| assertNotAlmostEqual(a, b) | round(a-b, 7) != 0                                                            |        |
| assertGreater(a, b)        | a > b                                                                         | 3.1    |
| assertGreaterEqual(a, b)   | a >= b                                                                        | 3.1    |
| assertLess(a, b)           | a < b                                                                         | 3.1    |
| assertLessEqual(a, b)      | a <= b                                                                        | 3.1    |
| assertRegex(s, r)          | r.search(s)                                                                   | 3.1    |
| assertNotRegex(s, r)       | not r.search(s)                                                               | 3.2    |
| assertCountEqual(a, b)     | a and b have the same elements in the same number, regardless of their order. | 3.2    |