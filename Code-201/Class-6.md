# Class 6 - Problem Domain, Objects, and the DOM

## Object Basics

1. How would you describe an ***object*** to a non-technical friend you grew up with?
   * My dear friend, an object is a collection of related information. When paired together, they're called ***properties*** and ***methods***.
2. What are some advantages to creating object literals?
   * Creating object literals is a quick, flexible way to create single objects and can be input easily into code.
3. How do objects differ from arrays?
   * Arrays are a sequential list of values, while objects can store a much larger collection of data and can be multi-dimensional.
4. Give an example for when you would need to use bracket notation to access an object’s property instead of dot notation.
   * If an object property name is held in a variable, then bracket notation would be used instead of dot notation (which wouldn't work).
5. Evaluate the code below. What does the term `this` refer to and what is the advantage to using `this`?
   * It refers to the current object where the `this` resides, which in this case is `dog`. This is useful if you're using the same code to create multiple objects and don't want to change the object name inside the code each time.

```
const dog = {
  name: 'Spot',
  age: 2,
  color: 'white with black spots',
  humanAge: function (){
    console.log(`${this.name} is ${this.age*7} in human years`);
  }
}
```

## Introduction To The DOM

1. What is the DOM?
   * "The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects; that way, programming languages can interact with the page." <https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction>
2. Briefly describe the relationship between the DOM and JavaScript.
   * "The code is written in JavaScript, but uses the DOM to access the document and its elements. The DOM is not a programming language, but without it, the JavaScript language wouldn't have any model or notion of web pages, HTML documents, SVG documents, and their component parts. The document as a whole, the head, tables within the document, table headers, text within the table cells, and all other elements in a document are parts of the document object model for that document. They can all be accessed and manipulated using the DOM and a scripting language like JavaScript." <https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction>
