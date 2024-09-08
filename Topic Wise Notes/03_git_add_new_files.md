## Git Adding New Files

So let's add some files, or create a new file using our favourite text editor. Then save or move it to the folder we just created.

Let's go back to the terminal and list the files in our current working directory:

```
ls
```
`ls` will list the files in the directory.

Then we check the Git status and see if it is a part of our repo:

```
git status
```

Now Git is aware of the file, but has not added it to our repository!

Files in your Git repository folder can be in one of 2 states:

    1. Tracked - files that Git knows about and are added to the repository
    2. Untracked - files that are in our working directory, but not added to the repository

 When we first add files to an empty repository, they are all untracked. To get Git to track them, we need to stage them, or add them to the staging environment.

 ## Git Staging Environment

 One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As we are working, we may be adding, editing and removing files. But whenever we hit a milestone or finish a part of the work, we should add the files to a Staging Environment.

Staged files are files that are ready to be committed to the repository we are working on.

Example:
```
git add <filename>
```

he file should be Staged. Let's check the status::
```
git status
```
Now the file has been added to the Staging Environment.

## Git Add More than One File
```
git add --all
```

Using `--all` instead of individual filenames will `stage` all changes (new, modified, and deleted) files.

Note: The shorthand command for `git add --all` is `git add -A`