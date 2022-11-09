# Passing Functions as Props

## React Docs - Lists and Keys

1. What does .map() return?
   * A new, modified array based on the function applied.
2. If I want to loop through an array and display each value in JSX, how do I do that in React?
   * Map each value to a new array and then put that array in curly brackets and insert it in the desired location in JSX.
3. Each list item needs a unique ____.
   * key
4. What is the purpose of a key?
   * Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.
   <https://reactjs.org/docs/lists-and-keys.html>

## The Spread Operator

1. What is the spread operator?
   * The spread operator is a useful and quick syntax for adding items to arrays, combining arrays or objects, and spreading an array out into a function’s arguments.
   <https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab>
2. List 4 things that the spread operator can do.
   * Copying an array
   * Concatenating or combining arrays
   * Using Math functions
   * Using an array as arguments
   * Adding an item to a list
   * Adding to state in React
   * Combining objects
   * Converting NodeList to an array  
   <https://reactjs.org/docs/lists-and-keys.html>
3. Give an example of using the spread operator to combine two arrays.  
<https://reactjs.org/docs/lists-and-keys.html>

```
const myArray = [`🤪`,`🐻`,`🎌`]
const yourArray = [`🙂`,`🤗`,`🤩`]
const ourArray = [...myArray,...yourArray]
console.log(...ourArray) // 🤪 🐻 🎌 🙂 🤗 🤩
```

4. Give an example of using the spread operator to add a new item to an array.
<https://reactjs.org/docs/lists-and-keys.html>

```
const fewFruit = ['🍏','🍊','🍌']
const fewMoreFruit = ['🍉', '🍍', ...fewFruit]
console.log(fewMoreFruit) //  Array(5) [ "🍉", "🍍", "🍏", "🍊", "🍌" ]
```

5. Give an example of using the spread operator to combine two objects into one.
<https://reactjs.org/docs/lists-and-keys.html>

```
const objectOne = {hello: "🤪"}
const objectTwo = {world: "🐻"}
const objectThree = {...objectOne, ...objectTwo, laugh: "😂"}
console.log(objectThree) // Object { hello: "🤪", world: "🐻", laugh: "😂" }
const objectFour = {...objectOne, ...objectTwo, laugh: () => {console.log("😂".repeat(5))}}
objectFour.laugh() // 😂😂😂😂😂
```

## How to Pass Functions Between Components

1. In the video, what is the first step that the developer does to pass functions between components?
   * Declare the function in the component where the state is going to change.
2. In your own words, what does the increment function do?
   * Takes in a "name" to compare. Creates a new array called "ppl" using the map method from the "people" array. Compares each index's name to see if it matches "name",]. If it does, then increases the count by 1. Then adds the updated name and count to the new array. Then it updates the "state" by replacing the old "people" array with the new array "ppl".
3. How can you pass a method from a parent component into a child component?
   * Just like any other prop, within the desired component declaration you give the prop a name and assign it `{this.(function name)}` with the function name being declared in the same component.
4. How does the child component invoke a method that was passed to it from a parent component?
   * In the location you want to invoke the function, pass in `this.props.(function name)(argument)`.
