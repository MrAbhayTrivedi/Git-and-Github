# Git Push to GitHub

## Push Changes to GitHub

Let's try making some changes to our local git and pushing them to GitHub.

Commit the changes:
```
git commit -a -m "Updated index.html. Resized image"
[master e7de78f] Updated index.html. Resized image
 1 file changed, 1 insertion(+), 1 deletion(-)
```
And check the status:
```
git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Now push our changes to our remote origin:
```
git push origin
Enumerating objects: 9, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 16 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 578 bytes | 578.00 KiB/s, done.
Total 5 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/w3schools-test/hello-world.git
   5a04b6f..facaeae  master -> master
```
Go to GitHub, and confirm that the repository has a new commit:

