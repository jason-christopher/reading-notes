# Testing and Modules

## TDD

* TDD - Test-Driven Development is a strategy to  write tests first.
* Things to consider when writing tests:
  * The test name should be descriptive and say what is expected and what we are testing.
  * Arrange - you need to organize the data needed to execute that piece of code (input)
  * Act - here you will execute the code being tested (exercise the behavior)
  * Assert - after executing the code, you will check if the result (output) is the same as you were expecting.
* The cycle:
  * Write a unit test and make it fail
  * Write the feature and make the test pass
  * Refactor the code — the first version doesn’t need to be the beautiful one
* The greatest advantage about TDD is to craft the software design first
* Your code will be more reliable: after a change you can run your tests and be in peace.  

Source: <https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932>

## `__name__` = `"__main__"`

* If the python interpreter is running that module (the source file) as the main program, it sets the special __name__ variable to have a value “__main__”.
* If this file is being imported from another module, __name__ will be set to the module’s name. Module’s name is available as value to __name__ global variable.  

Source: <https://www.geeksforgeeks.org/what-does-the-if-__name__-__main__-do/>

## Recursion

* Recursion - The process in which a function calls itself directly or indirectly. The corresponding function is called a recursive function.
* Recursion can reduce the length of our code and make it easier to read and write.
* Properties of recursion:
  * Performing the same operations multiple times with different inputs.
  * In every step, we try smaller inputs to make the problem smaller.
  * Base condition is needed to stop the recursion otherwise infinite loop will occur.
* If the base case is not reached or not defined, then the stack overflow problem may arise.
* A function is called ***direct recursive*** if it calls the same function.
* A function is called ***indirect recursive*** if it calls another function directly or indirectly.  

Source: <https://www.geeksforgeeks.org/introduction-to-recursion-data-structure-and-algorithm-tutorials/>
