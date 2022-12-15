# Command Line Practice

## The Command Line

* A command line, or terminal, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.
* Within a terminal you have what is known as a shell. This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you. There are various shells available but the most common one is called bash which stands for Bourne again shell.
* If you would like to know which shell you are using you may use a command called echo to display a system variable stating your current shell. echo is a command which is used to display messages.  

Source: <https://ryanstutorials.net/linuxtutorial/commandline.php>

## Basic Navigation

* Root Directory - the very top of a structure
* Absolute Path - specifies a location (file or directory) in relation to the root directory. You can identify them easily as they always begin with a forward slash ( / )
* Relative Path - specifies a location (file or directory) in relation to where we currently are in the system. They will not begin with a slash.
* `pwd` - ***Print Working Directory***. The command tells you what your current or present working directory is.
* `ls` - ***List***. Lists contents of current directory.
  * `ls -l` - long listing
  * `ls /etc` - tells `ls` not to list our current directory but instead to list that directories contents
* `~` - shortcut for your home directory
* `.` - reference to your current directory
* `..` - reference to the parent directory
* `cd [location]` - Change Directory. Moves to another directory listed in `[location]`.  

Source: <https://ryanstutorials.net/linuxtutorial/navigation.php>

## More About Files

* Under the hood, everything is actually a file.
* Linux systems ignore the file extension and looks inside the file to determine what type of file it is.
* Linux is case-sensitive.
* Spaces can be used in file names, but must be used with `' '` quotes around the name or `\` escape characters before the space.
* Hidden files in Linux begin with a `.` and the command line option `-a` must be used to view them.  

Source:  <https://ryanstutorials.net/linuxtutorial/aboutfiles.php>

## Manual Pages

* Manual pages are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept.
* `man <command to look up>` - invoke the manual pages
* To exit the man pages press `q` for quit.
* `man -k <search term>` - keyword search on the manual pages
* `/<term>` - within a manual page, perform a search for 'term'
* `n` - after performing a search within a manual page, select the next found item

Source:  <https://ryanstutorials.net/linuxtutorial/manual.php>

## File Manipulation

* `mkdir [options] <Directory>` - ***Make Directory***. Creates a directory within the name specified in the `<Directory>` portion.
  * `-p` - tells mkdir to make parent directories as needed
  * `-v` - makes mkdir tell us what it is doing
* `rmdir` - ***Remove Directory***. Deletes a directory.
* `touch` - creates a blank file
* `cp` - ***Copy***. Copies a file or directory.
* `mv` - ***Move***. Moves a file or directory (can also be used to rename).
* `rm` - ***Remove***. Deletes a file.
* The Linux command line does not have an undo feature
* Most commands have many useful command line options that can be found in the manual page

Source: <https://ryanstutorials.net/linuxtutorial/filemanipulation.php>

## Cheat Sheet

* <https://ryanstutorials.net/linuxtutorial/cheatsheet.php>
