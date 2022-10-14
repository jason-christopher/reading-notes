# Class 10 - Debugging

## Troubleshooting JavaScript

1. Name some key differences between a Syntax Error and a Logic Error.
   * Syntax errors: These are spelling errors in your code that actually cause the program not to run at all, or stop working part way through — you will usually be provided with some error messages too. These are usually okay to fix, as long as you are familiar with the right tools and know what the error messages mean!
   * Logic errors: These are errors where the syntax is actually correct but the code is not what you intended it to be, meaning that program runs successfully but gives incorrect results. These are often harder to fix than syntax errors, as there usually isn't an error message to direct you to the source of the error.
   <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_went_wrong>
2. List a few types of errors that you have encountered in past lab assignments and explain how you were able to correct them.
   * I had a syntax error when naming one of my functions. When I invoked the function, the code couldn't find a match so the code didn't run. It took me a while of going line-by-line to find the bug and make the simple correction.
3. How will this topic continue to influence your long term goals?
   * Debugging will always be a part of software development, so understanding errors and best practices for correcting these bugs will always be valuable.

## The JavaScript Debugger

1. How would you describe the JavaScript Debugger tool and how it works to someone just starting out in software development?
   * The JavaScript debugger allows you to set breakpoints. These are places in the code where execution stops in order to view individual variables and their values to see if there are any errors.
2. Define what a breakpoint is.
   * Places in the code where execution stops in order to view individual variables and their values to see if there are any errors.
3. What is the call stack?
   * The Call stack section shows you what code was executed to get to the current line. You can see that the code is in the function that handles a mouse click, and that the code is currently paused on the breakpoint. <https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools#the_javascript_debugger>
