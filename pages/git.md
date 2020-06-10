# Git

This is a collection of the most commonly used git commands while developing software, serving as both a reference, as well as an 80/20 approach for the vast array of options available with the most popular version-control system.

Created in 2005 by Linus Torvalds, git means different things to many a developer. Its README explains all:

“git” can mean anything, depending on your mood:
* Random three-letter combination that is pronounceable, and not actually used by any common UNIX command. The fact that it is a mispronounciation of “get” may or may not be relevant.
* Stupid. Contemptible and despicable. Simple. Take your pick from the dictionary of slang.
* “Global Information Tracker”: you’re in a good mood, and it actually works for you. Angels sing, and a light suddenly fills the room.
* “Goddamn idiotic truckload of sh*t”: when it breaks.

> "This is a stupid (but extremely fast) directory content manager. It doesn’t do a whole lot, but what it does do is track directory contents efficiently."  
> – Linus Torvalds

## Table of Contents
1. [Initializing](#initializing)
1. [Remotes](#remotes)
1. [Adding](#adding)
1. [Undoing](#undoing)
1. [Rebasing](#rebasing)
1. [Blaming](#blaming)
1. [Renaming](#renaming)  
1. [History](#history)

## Initializing
```bash
git init
git add README.md
git commit -m "Initial commit"
git remote add origin git@github.com:username/repo.git
git push -u origin master
```

## Remotes
```bash
git remote add origin username@github.git
git remote -v
```

## Adding
```bash
git add .
git add file
git add -p
```

## Undoing
```bash
git reset HEAD~
git reset --hard HEAD~1 
git reset --soft HEAD~1
```

## Rebasing
When creating a Pull Request, and iterating on the branch based on push-back from peers, rebasing code onto another branch keeps the commit history clean and readable.  
```bash
git log --graph --decorate --pretty=oneline --abbrev-commit
git rebase -i HEAD~<number>
squash
git push origin feature --force
```

## Blaming
```bash
git blame file
```

## Renaming
```bash
git branch -m new-name
```

## History
To view the history of changes to a file:
```bash
git log -p filename
git show HEAD s
```