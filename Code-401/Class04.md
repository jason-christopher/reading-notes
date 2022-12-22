# Classes & Objects, Thinking Recursively, and Pytest Fixtures & Coverage

## Classes & Objects

* Objects are an encapsulation of variables and functions into a single entity.
* Objects get their variables and functions from classes.
* Classes are essentially a template to create your objects.
* You can create multiple different objects that are of the same class(have the same variables and functions defined); however, each object contains independent copies of the variables defined in the class.

### `init()`

* The `__init__()` function, is a special function that is called when the class is being initiated. It's used for assigning values in a class.

```
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

car1 = Vehicle()
car1.name = "Fer"
car1.color = "red"
car1.kind = "convertible"
car1.value = 60000.00

print(car1.description())
```

Source: <https://www.learnpython.org/en/Classes_and_Objects>

***

## Thinking Recursively

* A recursive function is a function defined in terms of itself via self-referential expressions.
* This means that the function will continue to call itself and repeat its behavior until some condition is met to `return` a result.
* All recursive functions share a common structure made up of two parts: base case and recursive case.

### Maintaining State

When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:

  1. Thread the state through each recursive call so that the current state is part of the current call’s execution context.
  2. Keep the state in global scope.

### Recursive Data Structures in Python

A data structure is recursive if it can be defined in terms of a smaller version of itself. A list, set, tree, and dictionary are all examples of a recursive data structure.

Source: <https://realpython.com/python-thinking-recursively/>

***

## Pytest Fixtures & Coverage

### Fixtures

* When you're writing tests, you're going to write an entire "test suite", with each test aiming to check a different path through your code. In many cases, this means you'll have a few tests with similar characteristics, something that pytest handles with ***parametrized tests***.
* In pytest, you define fixtures using a combination of the `pytest.fixture` decorator, along with a function definition:

```
@pytest.fixture
def simple_file():
   return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))
```

* Fixtures are used differently from global variables.
* Your fixture might act like data, in that you don't invoke it with parentheses. But it's actually a function under the hood, which means it executes every time you invoke a test using that fixture. This means that the fixture, in contrast with regular-old data, can make calculations and decisions.
* You also can decide how often a fixture is run. If you want to set up an object and then use it multiple times without creating it again, you can do that by setting the fixture's ***scope***. You set the scope of the fixture to be ***module***, it'll be available throughout your tests but will execute only a single time. You can do this by passing the scope parameter to the `@pytest.fixture` decorator:

```
@pytest.fixture(scope='module')
def simple_file():
   return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))
```

* This particular fixture ***module*** scope is a bad idea, since the second test will end up having a `StringIO` whose location pointer (checked with `file.tell`) is already at the end.
* If your fixture uses `yield` instead of `return`, pytest understands that the post-yield code is for tearing down objects and connections.
* If your fixture has ***module*** scope, pytest will wait until all of the functions in the scope have finished executing before tearing it down.

### Coverage

* There's always the question of how thoroughly you have tested your code.
* 100% code coverage doesn't mean that your code is perfect or that it lacks bugs. But it does give you a greater degree of confidence in the code and the fact that it has been run at least once.
* So, how can you include code coverage with pytest? It turns out that there's a package called pytest-cov on PyPI that you can download and install. Once that's done, you can invoke pytest with: `pytest --cov=mymul .`
* Once you've done this, you'll need to turn the coverage report into something human-readable: `coverage html`
* This creates a directory called `htmlcov`. Open the index.html file in this directory using your browser, and you'll get a web-based report showing (in red) where your program still lacks coverage.

Source: <https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage>
