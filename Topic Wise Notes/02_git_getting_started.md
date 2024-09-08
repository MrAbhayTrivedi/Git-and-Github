# Git Getting Started

## Git Install
You can download Git for free from the following website: https://www.git-scm.com/

## Using Git with Command Line
The first thing we need to do, is to check if Git is properly installed:

```
git --version
```

If Git is installed, it should show something like git version X.Y


## Configure Git

```
git config --global user.name "your-name"
git config --global user.email "your-email"
```

Note: Use global to set the username and e-mail for every repository on your computer.

If you want to set the username/e-mail for just the current repo, you can remove global

## Creating Git Folder

```
mkdir myproject
cd myproject
```

Now that we are in the correct directory. We can start by initializing Git!

## Initialize Git

```
git init 
```
Note: Git now knows that it should watch the folder you initiated it on.

Git creates a hidden folder to keep track of changes.