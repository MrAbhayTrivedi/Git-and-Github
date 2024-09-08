# Git Commit

Since we have finished our work, we are ready move from stage to commit for our repo.

Adding commits keep track of our progress and changes as we work. Git considers each commit change point or "save point". It is a point in the project we can go back to if we find a bug, or want to make a change.

When we commit, we should always include a message.

By adding clear messages to each commit, it is easy for ourself (and others) to see what has changed and when.

```
git commit -m "Your message"
```

The commit command performs a commit, and the -m "message" adds a message.

## Git Commit without Stage

Sometimes, when we make small changes, using the staging environment seems like a waste of time. It is possible to commit changes directly, skipping the staging environment. The `-a` option will automatically stage every changed, already tracked file.

We can use the --short option to see the changes in a more compact way:
```
git status --short
```

Note: Short status flags are:

    * ?? - Untracked files
    * A - Files added to stage
    * M - Modified files
    * D - Deleted files

We see the file we expected is modified. So let's commit it directly:

```
git commit -a -m "Your new message"
```

Warning: Skipping the Staging Environment is not generally recommended.

Skipping the stage step can sometimes make us include unwanted changes.

## Git Commit Log

To view the history of commits for a repository, you can use the `log` command:

```
git log
```
