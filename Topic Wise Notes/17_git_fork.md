# Git GitHub Fork

## Add to Someone Else's Repository
At the heart of Git is collaboration. However, Git does not allow you to add code to someone else's repository without access rights.

## Fork a Repository
A `fork` is a copy of a repository. This is useful when you want to contribute to someone else's project or start your own project based on theirs.

`fork` is not a command in Git, but something offered in GitHub and other repository hosts.

## Clone a Fork from GitHub
A `clone` is a full copy of a repository, including all logging and versions of files.

Move back to the original repository, and click the green "Code" button to get the `URL` to `clone`.

Open your Git bash and clone the repository:
```
git clone <URL>
```
Take a look in your file system, and you will see a new directory named after the cloned project:
```
ls
```
### Note: To specify a specific folder to clone to, add the name of the folder after the repository `URL`, like this: `git clone <URL> myfolder`

Navigate to the new directory, and check the `status`:
```
cd myfolder
git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

And check the `log` to confirm that we have the full repository data:
```
git log
commit 0000000000000000000000000000000000000000 (HEAD -> master, origin/master, origin/HEAD)
Author: <your name> <<your email>>
Date:   Thu Jan 1 00:00:00 1970 +0000
    Initial commit
...
```
Now we have a full copy of the original repository.

## Configuring Remotes

Basically, we have a full copy of a repository, whose `origin` we are not allowed to make changes to.

```
git remote -v
origin  https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
origin  https://github.com/w3schools-test/w3schools-test.github.io.git (push)
```

We see that `origin` is set up to the original `"w3schools-test"` repository, we also want to add our own `fork`.

First, we `rename` the original `origin` `remote`:

```
git remote rename origin upstream
git remote -v
upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
```
Then fetch the `URL` of our own `fork`:

And add that as `origin`:
```
git remote add origin https://github.com/kaijim/w3schools-test.github.io.git
git remote -v
origin  https://github.com/kaijim/w3schools-test.github.io.git (fetch)
origin  https://github.com/kaijim/w3schools-test.github.io.git (push)
upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
```

### Note: According to Git naming conventions, it is recommended to name your own repository `origin`, and the one you forked for `upstream`

Now we have 2 remotes:

* `origin` - our own `fork`, where we have read and write access
* `upstream` - the original, where we have read-only access