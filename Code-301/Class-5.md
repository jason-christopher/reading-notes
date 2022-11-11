# Putting It All Together

## React Docs - Thinking in React

1. What is the `single responsibility principle` and how does it apply to components?
   * A component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller sub-components.  
   <https://reactjs.org/docs/thinking-in-react.html>
2. What does it mean to build a ‘static’ version of your application?
   * A version that takes your data model and renders the UI but has no interactivity.  
   <https://reactjs.org/docs/thinking-in-react.html>
3. Once you have a static application, what do you need to add?
   * The minimal set of mutable state that your app needs.  
   <https://reactjs.org/docs/thinking-in-react.html>
4. What are the three questions you can ask to determine if something is state?
   1. Is it passed in from a parent via props? If so, it probably isn’t state.
   2. Does it remain unchanged over time? If so, it probably isn’t state.
   3. Can you compute it based on any other state or props in your component? If so, it isn’t state.
   <https://reactjs.org/docs/thinking-in-react.html>
5. How can you identify where state needs to live?
   1. Identify every component that renders something based on that state.
   2. Find a common owner component (a single component above all the components that need the state in the hierarchy).
   3. Either the common owner or another component higher up in the hierarchy should own the state.
   4. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.  
    <https://reactjs.org/docs/thinking-in-react.html>

## Higher-Order Functions

1. What is a “higher-order function”?
   * Functions that operate on other functions, either by taking them as arguments or by returning them.
   <https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK>
2. Explore the `greaterThan` function as defined in the reading. In your own words, what is line 2 of this function doing?
   * It is creating an additional function within greaterThan to compare a value "m" against the argument "n" to compare. Based on if "m" is greater than "n", the function will return a boolean value `true` or `false`. In order to call greaterThan and have it compare, an additional argument is required to be passed into the function. For example, `greaterThan(10)(20)` would return `true`, but `greaterThan(10)(5)` would return `false`.
3. Explain how either `map` or `reduce` operates, with regards to higher-order functions.
   * `map` is a method that can applied to arrays to iterate through each index of the array to apply some function and return a new array. `map` requires an additional function to be passed in the argument to apply to each index value of the array. For example, in the code below, the `map` method would create a new array called `newArr` that would have the value of `[4,12,2,16]`.

   ```
   let arr = [ 2, 6, 1, 8];
   
   let newArr = arr.map(value => {
      return value*2;
   })
   ```
