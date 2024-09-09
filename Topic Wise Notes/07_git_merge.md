# Git Branch Merge

We have the emergency fix ready, and so let's merge the master and emergency-fix branches.

First, we need to change to the master branch:

For example,
```
git checkout master
Switched to branch 'master'
```
Now we merge the current branch (master) with emergency-fix:

For example,
```
git merge emergency-fix
Updating 09f4acd..dfa79db
Fast-forward
 index.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
 ```
 Since the emergency-fix branch came directly from master, and no other changes had been made to master while we were working, Git sees this as a continuation of master. So it can "Fast-forward", just pointing both master and emergency-fix to the same commit.

As master and emergency-fix are essentially the same now, we can delete emergency-fix, as it is no longer needed:

For example,
```
git branch -d emergency-fix
Deleted branch emergency-fix (was dfa79db).
```

## Merge Conflict

Now we can move over to hello-world-images and keep working. Add another image file (img_hello_git.jpg) and change index.html, so it shows it:

```
git checkout hello-world-images
Switched to branch 'hello-world-images'
```

Now, we are done with our work here and can stage and commit for this branch:

For example,
```
git add --all
git commit -m "added new image"
[hello-world-images 1f1584e] added new image
 2 files changed, 1 insertion(+)
 create mode 100644 img_hello_git.jpg
```

We see that index.html has been changed in both branches. Now we are ready to merge hello-world-images into master. But what will happen to the changes we recently made in master?

For example,
```
git checkout master
git merge hello-world-images
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

The merge failed, as there is conflict between the versions for index.html. Let us check the status:

```
git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   img_hello_git.jpg
        new file:   img_hello_world.jpg

Unmerged paths:
  (use "git add ..." to mark resolution)
        both modified:   index.html
```
This confirms there is a conflict in index.html, but the image files are ready and staged to be committed.

So we need to fix that conflict. Open the file in our editor:

```
<!DOCTYPE html>
<html>
<head>
<title>Hello World!</title>
<link rel="stylesheet" href="bluestyle.css">
</head>
<body>

<h1>Hello world!</h1>
<div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:960px"></div>
<p>This is the first file in my new Git Repo.</p>
<<<<<<< HEAD
<p>This line is here to show how merging works.</p>
=======
<p>A new line in our file!</p>
<div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>
>>>>>>> hello-world-images

</body>
</html>
```
We can see the differences between the versions and edit it like we want:
``` 
<!DOCTYPE html>
<html>
<head>
<title>Hello World!</title>
<link rel="stylesheet" href="bluestyle.css">
</head>
<body>

<h1>Hello world!</h1>
<div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:960px"></div>
<p>This is the first file in my new Git Repo.</p>
<p>This line is here to show how merging works.</p>
<div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>

</body>
</html>
```
Now we can stage index.html and check the status:

```
git add index.html
git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        new file:   img_hello_git.jpg
        new file:   img_hello_world.jpg
        modified:   index.html
```

The conflict has been fixed, and we can use commit to conclude the merge:
```
git commit -m "merged with hello-world-images after fixing conflicts"
[master e0b6038] merged with hello-world-images after fixing conflicts
```

And delete the hello-world-images branch:

```
git branch -d hello-world-images
Deleted branch hello-world-images (was 1f1584e).
```
