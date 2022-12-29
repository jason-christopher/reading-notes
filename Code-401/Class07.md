# Python Scope

* The concept of ***scope*** rules how variables and names are looked up in your code. It determines the visibility of a variable within the code.
* The letters in the acronym LEGB stand for ***Local, Enclosing, Global, and Built-in*** scopes.

## Understanding Scope

* Global scope: The names that you define in this scope are available to all your code.
* Local scope: The names that you define in this scope are only available or visible to the code within the scope.
* You can create Python names through one of the following operations:
  1. Assignments: x = value
  2. Import operations: import module or from module import name
  3. Function definitions: def my_func(): ...
  4. Argument definitions in the context of functions: def my_func(arg1, arg2,... argN): ...
  5. Class definitions: class MyClass: ...
* Python scopes are implemented as dictionaries that map names to objects. These dictionaries are commonly called ***namespaces***. These are the concrete mechanisms that Python uses to store names. They’re stored in a special attribute called .`__dict__`.

## Using the LEGB Rule for Python Scope

* ***Local (or function) scope*** is the code block or body of any Python function or lambda expression. This Python scope contains the names that you define inside the function. These names will only be visible from the code of the function. It’s created at function call, not at function definition, so you’ll have as many different local scopes as function calls. This is true even if you call the same function multiple times, or recursively. Each call will result in a new local scope being created.
* ***Enclosing (or nonlocal) scope*** is a special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function. This scope contains the names that you define in the enclosing function. The names in the enclosing scope are visible from the code of the inner and enclosing functions.
* ***Global (or module) scope*** is the top-most scope in a Python program, script, or module. This Python scope contains all of the names that you define at the top level of a program or a module. Names in this Python scope are visible from everywhere in your code.
* ***Built-in scope*** is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python. Names in this Python scope are also available from everywhere in your code. It’s automatically loaded by Python when you run a program or script.

## Modifying the Behavior of a Python Scope

* Python provides two keywords that allow you to modify the content of global and nonlocal names. These two keywords are:
  1. global
  2. nonlocal
  
  ```
  global counter  # Declare counter as global
  counter = counter + 1  # Successfully update the counter
  ```

  ```
  nonlocal var  # Try to use nonlocal in a local scope
  print(var)
  ```

## Using Enclosing Scopes as Closures

* ***Closures*** are a special use case of the enclosing Python scope. When you handle a nested function as data, the statements that make up that function are packaged together with the environment in which they execute. The resulting object is known as a closure. In other words, a closure is an inner or nested function that carries information about its enclosing scope, even though this scope has completed its execution.
