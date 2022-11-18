# In Memory Storage

## JavaScript Call Stack

1. What is a ‘call’?
   * When a function is invoked.
2. How many ‘calls’ can happen at once?
   * One
3. What does LIFO mean?
   * Last In, First Out: the last function that gets pushed into the stack is the first to be pop out, when the function returns.
4. Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.

```
    function firstFunction(){
      throw new Error('Stack Trace Error');
    }

    function secondFunction(){
      firstFunction();
    }
    
    function thirdFunction(){
      secondFunction();
    }
    
    thirdFunction();
```

5. What causes a Stack Overflow?
   * A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.  

<https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4>

## JavaScript error messages

1. What is a ‘reference error’?
   * When you try to use a variable that is not yet declared.
2. What is a ‘syntax error’?
   * When you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.
3. What is a ‘range error’?
   * When you try to manipulate an object with some kind of length and give it an invalid length.
4. What is a ‘type error’?
   * When the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.
