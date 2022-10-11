# Class 7 - Object-Oriented Programming, HTML Tables

## Domain Modeling

1. Explain why we need domain modeling.
   * Domain modeling is needed to show how multiple entities are connected and the relationships between those entities.

## HTML Table Basics

1. Why should tables not be used for page layouts?
   * Tables used as layouts will reduce the accessibility for visually-impaired users, they will create HTML code that is very hard to read due to excessive tags, and tables are not automatically responsive so extra measures are needed to get table layout styling to work correctly. <https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics>
2. List and describe 3 different semantic HTML elements used in an HTML `<table>`.
   * `<td>` - Table Data (the smallest container inside a table)
   * `<tr>` - Table Row (used to stop one row and start another)
   * `<th>` - Table Header (acts the same way as `<td>`, but identifies table headers)

## Introducing Constructors

1. What is a constructor and what are some advantages to using it?
   * A constructor is a function called using the `new` keyword and is used to create a new object, bind `this` to the new object, so you can refer to `this` in your constructor code, run the code in the constructor, and return the new object. <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics#introducing_constructors>
2. How does the term `this` differ when used in an object literal versus when used in a constructor?
   * `this` can be used for multiple different variable names when using a constructor.

## Object Prototypes Using A Constructor

1. Explain prototypes and inheritance via an analogy from your previous work experience. *NOTE: This is a very common front end developer interview question*
   * We would use a standard template when creating training documents that had default information that could be used for any training report, but could be modified to more better describe the student's performance. The template was a ***protoype*** and the instructor would ***inherit*** the default information, but had the option to modify portions.
