# Class 3 - HTML Lists, Control Flow with JS, and the CSS Box Model

## Ordered and Unordered lists

1. When should you use an ***unordered list*** in your HTML document?
   * When you have a list that doesn't need to be numbered.
2. How do you change the ***bullet style*** of unordered list items?
   * Use the `list-style-type` property.
3. When should you use an ***ordered list*** vs an ***unordered list*** in your HTML document?
   * Use an ordered list when there is a defined sequence to the list while an unordered list is used when there is no required sequence.
4. Describe two ways you can change the numbers on ***list items*** provided by an ***ordered list***?
   * Use the `type=""` attribute with `a` for lowercase letters or `I` for uppercase Roman numerals.

## The Box Model

1. Describe the CSS properties of `margin` and `padding` as characters in a story. What is their role in a story titled: “The Box Model”?
   * The `padding` is the yard around the house (the content) and the `margin` is the outermost land around the city walls (the border), which encompasses the many yards (padding) and houses (content) in the city.
2. List and describe the four parts of an HTML elements box as referred to by the ***box model***.
   * The ***content*** is the center of the "box", surrounded by whitespace called the ***padding***. Surrounding the padding is the ***border***, which has additional whitespace around it called the ***margin***.

## Arrays. Operators and Expressions. Conditionals. Loops

1. What ***data types*** can you store inside of an ***Array***?
   * Strings, numbers, objects, and other arrays.
2. Is the `people` array a valid JavaScript array? If so, how can I access the values stored? If not, why?
   * Yes, it is valid and can be accessed by calling the desired index of `people`.

   ```
   const people = [['pete', 32, 'librarian', null], ['Smith', 40, 'accountant', 'fishing:hiking:rock_climbing'], ['bill', null, 'artist', null]];  
   ```

3. List five shorthand operators for assignment in javascript and describe what they do.
   * `+=` - Addition Assignment (`x = x + f()`)
   * `%=` -  Remainder Assignment (`x = x % f()`)
   * `<<=` - Left Shift Assignment (`x = x << f()`)
   * `||=` - Logical OR Assignment (`x || (x = f())`)
   * `**=` - Exponentiation Assignment (`x = x ** f()`)
4. Read the code below and evaluate the last ***expression*** and explain what the result would be and why.
   * `10dog`, because the `10 + false` would result in `10` which is a number. And the `(10) + 'dog'` would result in `10dog` which would be a string.

   ```
   let a = 10;
   let b = 'dog';
   let c = false;

   // evaluate this
   (a + c) + b;
   ```

5. Describe a real world example of when a conditional statement should be used in a JavaScript program.
   * When evaluating whether a value is greater than 0.
6. Give an example of when a ***Loop*** is useful in JavaScript.
   * When evaluating every index of a large array to reduce the amount of required code.
