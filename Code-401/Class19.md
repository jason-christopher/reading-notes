# Automation

## Regular Expressions

* A RegEx, or Regular Expression, is a sequence of characters that forms a search pattern.
* RegEx can be used to check if a string contains the specified search pattern.
* In Python, regular expressions are supported by the `re` module, so you have to import this module with `import re`.

### Functions

* `re.match(pattern, sequence)` - Will search the regular expression pattern and return the first occurrence or else returns `None`. Checks for a match ***only at the beginning of the string***. So, if a match is found in some other line, it returns `None`.
* `re.search(pattern, sequence)` - Will search the regular expression pattern and return the first occurrence. Unlike Python `re.match()`, ***it will check all lines of the input string***. Returns a match object when the pattern is found and `None` if the pattern is not found.
* `re.findall(pattern, sequence)` - Used to search for “all” occurrences that match a given pattern. In contrast, `search()` module will only return the first occurrence that matches the specified pattern. Will iterate over all the lines of the file and will return all non-overlapping matches of pattern as a ***list*** or returns an ***empty list*** if not found.
* `split(pattern, sequence, maxsplit)` - Returns a list where the string has been split at each match. You can control the number of split occurrences by specifying the `maxsplit` parameter.
* `sub(pattern, replacement, string, count)` - Replaces the matches with the replacement text of your choice. The text to be considered is the third argument `string` and you can control the number of replacements by specifying the `count` parameter.

### Special Characters

* `[]` - A set of characters `"[a-m]"`
* `\` - Signals a special sequence (can also be used to escape special characters `"\d"`
* `.` - Any character (except newline character) `"he..o"`
* `^` - Starts with `"^hello"`
* `$` - Ends with `"planet$"`
* `*` - Zero or more occurrences `"he.*o"`
* `+` - One or more occurrences `"he.+o"`
* `?` - Zero or one occurrences `"he.?o"`
* `{}` - Exactly the specified number of occurrences `"he.{2}o"`
* `|` - Either or `"falls|stays"`
* `()` - Capture and group
* `\A` - Returns a match if the specified characters are at the beginning of the string
* `\b` - Returns a match where the specified characters are at the beginning or at the end of a word
* `\B` - Returns a match where the specified characters are present, but NOT at the beginning (or at the end) of a word
* `\d` - Returns a match where the string contains digits (numbers from 0-9)
* `\D` - Returns a match where the string DOES NOT contain digits
* `\s` - Returns a match where the string contains a white space character
* `\S` - Returns a match where the string DOES NOT contain a white space character
* `\w` - Returns a match where the string contains any word characters (characters from a to Z, digits from 0-9, and the underscore _ character)
* `\W` - Returns a match where the string DOES NOT contain any word characters
* `\Z` - Returns a match if the specified characters are at the end of the string
* `[arn]` - Returns a match where one of the specified characters (a, r, or n) is present
* `[a-n]` - Returns a match for any lower case character, alphabetically between a and n
* `[^arn]` - Returns a match for any character EXCEPT a, r, and n
* `[0123]` - Returns a match where any of the specified digits (0, 1, 2, or 3) are present
* `[0-9]` - Returns a match for any digit between 0 and 9
* `[0-5][0-9]` - Returns a match for any two-digit numbers from 00 and 59
* `[a-zA-Z]` - Returns a match for any character alphabetically between a and z, lower case OR upper case
* `[+]` - In sets, +, *, ., |, (), $,{} has no special meaning, so [+] means: return a match for any + character in the string

Source:<https://www.w3schools.com/python/python_regex.asp#split>  
Source: <https://www.guru99.com/python-regular-expressions-complete-tutorial.html>

## shutil

The shutil module offers a number of high-level operations on files and collections of files. In particular, functions are provided which support file copying and removal.

* `shutil.copyfileobj(fsrc, fdst)` - Copy the contents of the file-like object `fsrc` to the file-like object `fdst`.
* `shutil.copyfile(src, dst)` - Copy the contents (no metadata) of the file named `src` to a file named `dst` and return `dst` in the most efficient way possible. `src` and `dst` are path-like objects or path names given as strings.
* `shutil.copymode(src, dst)` - Copy the permission bits from `src` to `dst`. The file contents, owner, and group are unaffected. `src` and `dst` are path-like objects or path names given as strings.
* `shutil.copystat(src, dst)` - Copy the permission bits, last access time, last modification time, and flags from `src` to `dst`.
* `shutil.copy(src, dst)` - Copies the file `src` to the file or directory `dst`. `src` and `dst` should be path-like objects or strings. If `dst` specifies a directory, the file will be copied into `dst` using the base filename from `src`. If `dst` specifies a file that already exists, it will be replaced. Returns the path to the newly created file.
* `shutil.copy2(src, dst)` - Identical to `copy()` except that `copy2()` also attempts to preserve file metadata.
* `shutil.copytree(src, dst)` - Recursively copy an entire directory tree rooted at `src` to a directory named `dst` and return the destination directory. All intermediate directories needed to contain `dst` will also be created by default.
* `shutil.move(src, dst)` - Recursively move a file or directory (`src`) to another location (`dst`) and return the destination.
* `shutil.rmtree()` - Deletes any folder, file or directory.
* `shutil.disk_usage(path)` - Return disk usage statistics about the given `path` as a named tuple with the attributes total, used and free, which are the amount of total, used and free space, in bytes. `path` may be a file or a directory.
* `shutil.which()` - Returns the path to an executable application which would run if the given command cmd was called.

Source: <https://docs.python.org/3/library/shutil.html>  
Source: <https://www.askpython.com/python-modules/shutil-module>
