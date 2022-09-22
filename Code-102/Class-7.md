# Class 7 - Programming with JavaScript

## Control Flow

* **control flow** - The order in which the computer executes statements in a script. Code is run in order from the first line in the file to the last line, unless the computer runs across the structures that change the control flow, such as ***conditionals***, ***loops***, and ***functions***.

***

## Functions

* **function** - a block of code designed to perform a particular task and is executed when "something" ***invokes*** it (***calls it***)

```
function myFunction(p1, p2) {
  return p1 * p2;   // The function returns the product of p1 and p2
}
```

***

## Function Syntax

* a JavaScript function is defined with the `function` keyword, followed by a ***name***, followed by parentheses: `()`
* function names can contain letters, digits, underscores, and dollar signs (same rules as variables)
* the parentheses may include ***parameter*** names separated by commas:
`(parameter1, parameter2, ...)`
* the code to be executed by the function is placed inside curly brackets: `{}`
* function ***arguments*** (parameters) are the ***values*** received by the function when it is invoked, which behave as local variables

```
function name(parameter1, parameter2, parameter3) {
  // code to be executed
}
```

***

## Function Return

* when JavaScript reaches a `return` statement, the function will stop executing
* if the function was invoked from a statement, JavaScript will "return" to execute the code after the invoking statement
* Functions often compute a `return` value. The return value is "returned" back to the "caller":

```
let x = myFunction(4, 3);   // Function is called, return value will end up in x

function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}
```

The result in `x` will be `12`

***

## Invoking (Calling) a Function

* the code inside the function will execute when "something" invokes (calls) the function:
  * when an event occurs (when a user clicks a button)
  * when it is invoked (called) from JavaScript code
  * automatically (self invoked)
* accessing a function without `()` will return the function ***object*** instead of the function ***result***

```
function toCelsius(fahrenheit) {
  return (5/9) * (fahrenheit-32);
}
document.getElementById("demo").innerHTML = toCelsius;
```

***

## Variables

### Using a Function as a Variable

* functions can be used the same way as you use variables, in all types of formulas, assignments, and calculations

```
let text = "The temperature is " + toCelsius(77) + " Celsius";
```

### Local Variables

* variables declared within a JavaScript function, become ***LOCAL*** to the function
* local variables can only be accessed from within the function

```
// code here can NOT use carName

function myFunction() {
  let carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```

***

## Why Functions?

* you can reuse code: Define the code once, and use it many times
* you can use the same code many times with different arguments, to produce different results

***

## JavaScript Operators

* the ***assignment*** operator `=` assigns a value to a variable:

```
let x = 10;
```

* the ***addition*** operator `+` adds numbers:

```
let x = 5;
let y = 2;
let z = x + y;
```

* the ***multiplication*** operator `*` multiplies numbers:

```
let x = 5;
let y = 2;
let z = x * y;
```

***

## Types of JavaScript Operators

There are different types of JavaScript operators:

* Arithmetic Operators
* Assignment Operators
* Comparison Operators
* Logical Operators
* Conditional Operators
* Type Operators

***

## Arithmetic Operators

`+`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Addition  
`-`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Subtraction  
`*`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Multiplication  
`**`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Exponentiation (ES2016)  
`/`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Division  
`%`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modulus (Division Remainder)  
`++`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Increment  
`--`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Decrement  

***

## Assignment Operators

Operator&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Example&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Same As  
`=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = y  
`+=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x += y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x + y  
`-=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x -= y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x - y  
`*=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x *= y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x * y  
`/=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x /= y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x / y  
`%=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x %= y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x % y  
`**=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x **= y&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x = x ** y  

***

## Comparison Operators

Operator&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description  
`==`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;equal to  
`===`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;equal value and equal type  
`!=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;not equal  
`!==`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;not equal value or not equal type  
`>`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;greater than  
`<`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;less than  
`>=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;greater than or equal to  
`<=`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;less than or equal to  
`?`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ternary operator  

***

## Logical Operators

Operator&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Description  
`&&`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;logical and  
`||`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;logical or  
`!`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;logical not