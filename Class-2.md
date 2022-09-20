# Class 2 Notes

## Files

* Everything is a file in Linux (even directories)
* Linux is case-sensitive
* `file [path]` - obtain information about what type of file a file or directory is

## Basic Commands

* `pwd` - ***Print Working Directory*** tells you what directory you're currently in
* `ls` - ***lists*** the directories or files withtin your current directory
    * `ls -a` - shows ***all*** files in the directory, including hidden files
    * `ls -l` - shows the ***long*** list of files to include permissions and file type
    * `ls Documents` - ***Relative paths*** specify a location (file or directory) in relation to where we currently are in the system. They will not begin with a slash
    * `ls /home/ryan/Documents` - ***Absolute paths*** specify a location (file or directory) in relation to the root directory. You can identify them easily as they always begin with a forward slash ( / )
* `cd [location]` - ***Change Directory*** to...change the directory we want to be in
    * `cd ..` - Use two periods to go back to the directory directly above the current location.
    * Use x+1 periods to go back x directories
* `mv [file name] [file name]` - ***moves*** file from first location to second location. Second location can be a new location.
