# Class 3 - Revisions and the Cloud

## What is Git?

* Version control system that lets multiple users work on the same code
* Keeps track of changes and keeps all of your projects in one repository

## What is GitHub?

* An online place to store code to share with others
* If Git is the sport, GitHub is the arena
* Manages work with version control, reviewing changes, and keeps changes separate until you want to add them

## Commands for Cloning and Verifying Status

* `git clone [URL]` - takes the URL from GitHub and clones it to the local computer
* `git remote -v` - displays the URL of the GitHub repository
* `git status` - displays if there have been any changes
* `code .` - opens the current folder in the editor
* `git pull origin main` - ***pulls*** updated repository from GitHub
  * `git config pull.rebase false` - merges local/GitHub in case of error between local and GitHub files (may need to add a comment in the Merge file)

## Commands for ACP (Add, Commit, Push) Process

* `git add [file names]` - ***adds*** files to stage for the snapshot
  * `git add .` - adds everything to stage for the snapshot
* `git commit -m "[message text]"` - add ***message*** and ***commits*** for the snapshot
* `git push origin main` - ***pushes*** any new commits to GitHub

## Terms

* repository - a collection of files that will be used by Git. Repositories can be stored live on GitHub or on a local computer.
* States
  * Modified - file has been changed but not staged or committed
  * Staged - files have been added to the Index and ready to be committed
  * Committed - data is securely stored in a local database
* Local Git Repository Structure:
  * Working Directory - actual files reside here
  * Index - area used for staging
  * Head - most up-to-date commit
* Saving Changes
  * Tracked - tracked files can be modified, unmodified, or staged; they were part of the most recent file snapshot
  * Untracked - untracked files were not in the last snapshot and do not currently reside in the staging area

## Other Notes

* Give messages to commits that act as captions for your snapshot
* One project = one repository (unless very large project)
