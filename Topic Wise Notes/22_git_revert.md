# Git Revert

`revert` is the command we use when we want to take a previous `commit` and add it as a new `commit`, keeping the log intact.

Step 1: Find the previous `commit`:

![alt text](image-7.png)

Step 2: Use it to make a new `commit`:

![alt text](image-8.png)

Let's make a new `commit`, where we have "accidentally" deleted a file:

```
git commit -m "Just a regular update, definitely no accidents here..."
[master 16a6f19] Just a regular update, definitely no accidents here...
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 img_hello_git.jpg
 ```
 Now we have a part in our `commit` history we want to go back to. Let's try and do that with `revert`.

 ## Git Revert Find Commit in Log

 First thing, we need to find the point we want to return to. To do that, we need to go through the `log`.

To avoid the very long log list, we are going to use the `--oneline` option, which gives just one line per commit showing:

* The first seven characters of the `commit hash`
* the `commit` message
So let's find the point we want to `revert`:

```
git log --oneline
52418f7 (HEAD -> master) Just a regular update, definitely no accidents here...
9a9add8 (origin/master) Added .gitignore
...
```

We want to revert to the previous `commit`: `52418f7 (HEAD -> master) Just a regular update, definitely no accidents here...`, and we see that it is the latest `commit`.

## Git Revert HEAD

We revert the latest `commit` using git `revert HEAD` (`revert` the latest change,  and then `commit`), adding the option `--no-edit` to skip the commit message editor (getting the default `revert` message):

```
git revert HEAD --no-edit
```

Now let's check the `log` again:

```
git log --oneline
e56ba1f (HEAD -> master) Revert "Just a regular update, definitely no accidents here..."
52418f7 Just a regular update, definitely no accidents here...
9a9add8 (origin/master) Added .gitignore
...
```

### Note: To revert to earlier commits, use `git revert HEAD~x` (`x` being a number. 1 going back one more, 2 going back two more, etc.)