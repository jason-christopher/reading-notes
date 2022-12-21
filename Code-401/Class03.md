# FileIO & Exceptions

## Reading and Writing Files in Python

One of the most common tasks that you can do with Python is reading and writing files.

### What Is a File?

* A file is a contiguous set of bytes used to store data.
* Files on most modern file systems are composed of three main parts:
  1. **Header**: metadata about the contents of the file (file name, size, type, and so on)
  2. **Data**: contents of the file as written by the creator or editor
  3. **End of file (EOF)**: special character that indicates the end of the file
![File](https://files.realpython.com/media/FileFormat.02335d06829d.png)

* The file path is a string that represents the location of a file. It’s broken up into three major parts:
  1. Folder Path: the file folder location on the file system where subsequent folders are separated by a forward slash / (Unix) or backslash \ (Windows)
  2. File Name: the actual name of the file
  3. Extension: the end of the file path pre-pended with a period (.) used to indicate the file type
* The American Standards Association (ASA) standard states that line endings should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n). The ISO standard however allowed for either the CR+LF characters or just the LF character.
* The two most common encodings are the ASCII and UNICODE Formats. ASCII can only store 128 characters, while Unicode can contain up to 1,114,112 characters. ASCII is actually a subset of Unicode (UTF-8), meaning that ASCII and Unicode share the same numerical to character values.

### Opening and Closing a File in Python

* When you want to work with a file, the first thing to do is to open it. This is done by invoking the `open()` built-in function.
* When you’re manipulating a file, there are two ways that you can use to ensure that a file is closed properly, even when encountering an error. The first way to close a file is to use the `try-finally` block:  

```
reader = open('dog_breeds.txt')
try:
    # Further file processing goes here
finally:
    reader.close()
```

* The second way to close a file is to use the `with` statement. The with statement automatically takes care of closing the file once it leaves the with block, even in cases of error:

```
with open('dog_breeds.txt') as reader:
    # Further file processing goes here
```

* Other options for modes are fully documented online, but the most commonly used ones are the following:
  * `r`	 - Open for reading (default)
  * `w` -	Open for writing, truncating (overwriting) the file first
  * `rb` or `wb` - Open in binary mode (read/write using byte data)

### Reading and Writing Opened Files

* There are multiple methods that can be called on a file object to read a file once it is opened:
  * `.read(size=-1)` - This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.
  * `.readline(size=-1)` - This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.
  * `.readlines()` - This reads the remaining lines from the file object and returns them as a list.
* A common thing to do while reading a file is to iterate over each line:

```
>>> with open('dog_breeds.txt', 'r') as reader:
>>>     # Read and print the entire file line by line
>>>     for line in reader:
>>>         print(line, end='')
```

* As with reading files, file objects have multiple methods that are useful for writing to a file:
  * `.write(string)` - This writes the string to the file.
  * `.writelines(seq)` - This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).
* Here’s a quick example of using `.write()` and `.writelines()`:

```
with open('dog_breeds.txt', 'r') as reader:
    # Note: readlines doesn't trim the line endings
    dog_breeds = reader.readlines()

with open('dog_breeds_reversed.txt', 'w') as writer:
    # Alternatively you could use
    # writer.writelines(reversed(dog_breeds))

    # Write the dog breeds to the file in reversed order
    for breed in reversed(dog_breeds):
        writer.write(breed)
```

* The `__file__` attribute is a special attribute of modules, similar to `__name__`. It is the pathname of the file from which the module was loaded, if it was loaded from a file.

Source: <https://realpython.com/read-write-files-python/>

***

## Python Exceptions

In Python, an error can be a syntax error or an exception.

### Exceptions versus Syntax Errors

* Syntax errors occur when the parser detects an incorrect statement.
* Exception errors occur whenever syntactically correct Python code results in an error.

### Raising an Exception

* We can use `raise` to throw an exception if a condition occurs. The statement can be complemented with a custom exception:

```
x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
```

### The `AssertionError` Exception

* Instead of waiting for a program to crash midway, you can also start by making an assertion in Python. We `assert` that a certain condition is met. If this condition turns out to be `True`, then that is excellent! The program can continue. If the condition turns out to be `False`, you can have the program throw an `AssertionError` exception:

```
import sys
assert ('linux' in sys.platform), "This code runs on Linux only."
```

### The `try` and `except` Block: Handling Exceptions

* The `try` and `except` block in Python is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program. The code that follows the except statement is the program’s response to any exceptions in the preceding `try` clause.
* In this example, you call a function that you wrote yourself. When you execute the function, you catch the AssertionError exception and print it to screen.



```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
    print('The linux_interaction() function was not executed')
```

* To catch this type of exception and print it to screen, you could use the following code:

```
try:
    with open('file.log') as file:
        read_data = file.read()
except FileNotFoundError as fnf_error:
    print(fnf_error)
```

### The `else` Clause

* In Python, using the `else` statement, you can instruct a program to execute a certain block of code only in the absence of exceptions:

```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    print('Executing the else clause.')
```

### Cleaning Up After Using `finally`

* Imagine that you always had to implement some sort of action to clean up after executing your code. Python enables you to do so using the `finally` clause:

```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('Cleaning up, irrespective of any exceptions.')
```

Source: <https://realpython.com/python-exceptions/>
