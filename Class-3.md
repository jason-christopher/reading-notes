# Class 3 Notes

## What is Git?

* Version control system that lets multiple users work on the same code
* Keeps track of changes and keeps all of your projects in one repository

## What is GitHub?

* An online place to store code to share with others
* If Git is the sport, GitHub is the arena
* Manages work with version control, reviewing changes, and keeps changes separate until you want to add them

## Commands for Cloning and Verifying Status

* `git clone [URL]` - takes the URL from GitHub and clones it to the local computer
* `git remote -v` - see the URL of the GitHub repository
* `git status` - displays if there have been any changes
* `code .` - opens the current folder in the editor

## Commands for ACP (Add, Commit, Push) Process

* `git add [file names]` - adds files to stage for the snapshot
  * `git add .` - adds everything to stage for the snapshot
* `git commit -m "[message text]"` - add ***message*** to commit snapshot
* `git push origin main` - ***pushes*** any new commits (the snapshots of your code) to GitHub

## Terms

* repository - a collection of files that will be used by Git. Repositories can be stored live on GitHub or on a local computer.
* Commit - a "snapshot" of file
* Local Git Repository Structure:
  * Working Directory - actual files reside here
  * Index - area used for staging
  * Head - most up-to-date "commit"

## Other Notes

* Give messages to commits that act as captions for your snapshot
* One project = one repository (unless very large project)
