# React and Forms

## React Docs - Forms

1. What is a ‘Controlled Component’?
   * An input form element whose value is controlled by React.
2. Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.
   * Update the state with their responses as soon as they enter them so the new information can be used immediately.
3. How do we target what the user is entering if we have an event handler on an input field?
   * Use the onChange attribute to invoke a function that uses and "event" argument.

## The Conditional (Ternary) Operator Explained

1. Why would we use a ternary operator?
   * Makes a conditional statement on one line of code.
2. Rewrite the following statement using a ternary statement:

```
if(x===y){
  console.log(true);
} else {
  console.log(false);
}
```

* Ternary statement: `x === y ? console.log(true) : console.log(false);`
