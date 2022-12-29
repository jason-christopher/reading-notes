# List Comprehensions

Python provides a more concise method for handling lists and list comprehension. List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.

## Syntax

`my_new_list = [ expression for item in list ]`

* You can see from this example that three ingredients are necessary for a python list comprehension to work:
  1. First is the expression we’d like to carry out. expression inside the square brackets.
  2. Second is the object that the expression will work on. item inside the square brackets.
  3. Finally, we need an iterable list of objects to build our new list from. list inside the square brackets.
* List comprehension methods are an elegant way to create and manage lists.
* In Python, list comprehensions are a more compact way of creating lists.
* More flexible than for loops, list comprehension is usually faster than other methods.

## Create a List with `range()`

```
digits = [x for x in range(10)]
print(digits)
```

Output: `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`

* The first `x` is our expression. It doesn’t do anything because we’re simply recording the number. The second `x` represents each item in the list created by the `range()` method.

## Create a List Using Loops and List Comprehension in Python

```
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)
```

Output: `[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]`

The same thing can be done using a list comprehension, but with a fraction of the code:

```
squares = [x**2 for x in range(10)]
print(squares)
```

## Multiplying Parts of a List

```
multiples_of_three = [ x*3 for x in range(10) ]

print(multiples_of_three)
```

Output: `[0, 3, 6, 9, 12, 15, 18, 21, 24, 27]`

Adding a filter to the list comprehension allows for greater flexibility. By using filters, we can select certain items from the list, while excluding others:

`even_numbers = [ x for x in range(1,20) if x % 2 == 0]`

Output: `[2, 4, 6, 8, 10, 12, 14, 16, 18]`

## Show the first letter of each word using Python

### Using list comprehensions with strings

```
# a list of the names of popular authors
authors = ["Ernest Hemingway","Langston Hughes","Frank Herbert","Toni Morrison",
    "Emily Dickson","Stephen King"]

# create an acronym from the first letter of the author's names
letters = [ name[0] for name in authors ]
print(letters)
```

Output: `['E', 'L', 'F', 'T', 'E', 'S']`

### Separating the characters in a string

```
# use list comprehension to print the letters in a string
letters = [ letter for letter in "20,000 Leagues Under The Sea"]

print(letters)
```

Output: `['2', '0', ',', '0', '0', '0', ' ', 'L', 'e', 'a', 'g', 'u', 'e', 's', ' ', 'U', 'n', 'd', 'e', 'r', ' ', 'T', 'h', 'e', ' ', 'S', 'e', 'a']`

## Lower/Upper case converter using Python

```
lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]

print(lower_case, upper_case)
```

Output: `['a', 'b', 'c'] ['A', 'B', 'C']`

## Print numbers only from a given string

```
# user data entered as name and phone number
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]

print(phone_number)
```

Output: `['9', '8', '7', '6', '5', '4', '3', '2', '1', '0']`

## Parsing a file using list comprehension

```
# open the file in read-only mode
file = open("dreams.txt", 'r')
poem = [ line for line in file ]

for line in poem:
    print(line)
```

Output:

```
Hold fast to dreams

For if dreams die

Life is a broken-winged bird

That cannot fly.

-Langston Hughs
```

## Using functions in list comprehensions

Not only can we write our own functions with list comprehensions, but we can also add filters to better control the statements.

```
# list comprehension with functions
# create a function that returns a number doubled
def double(x):
    return x*2

nums = [double(x) for x in range(1,10)]
print(nums)
```

Output: `[2, 4, 6, 8, 10, 12, 14, 16, 18]`
