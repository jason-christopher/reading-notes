# Functional Programming

## Functional Programming Concepts

1. What is functional programming?
   * Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.  
   <https://en.wikipedia.org/wiki/Functional_programming>
2. What is a pure function and how do we know if something is a pure function?
   * It returns the same result if given the same arguments (it is also referred as `deterministic`)
   * It does not cause any observable side effects
3. What are the benefits of a pure function?
   * It is easier to test.
4. What is immutability?
   * The state cannot change after it’s created.
5. What is Referential transparency?
   * If a function consistently yields the same result for the same input, it is referentially transparent.  
<https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa>

## Node JS Tutorial for Beginners #6 - Modules and require()

1. What is a module?
   * A JavaScript file that has a specific functionality in the application.
2. What does the word ‘require’ do?
   * It lets you make a separate JS file global.
3. How do we bring another module into the file the we are working in?
   * `require('./<insert-file-name>);`
4. What do we have to do to make a module available?
   * `module.export = <insert-element-to-export>`
