# Git GitHub Add SSH

## Copy the SSH Public Key
In the previous chapter, we created an SSH key pair.

Now we will use the clip < command to copy the public key to our clipboard:

```
clip < /Users/user/.ssh/id_rsa.pub
```

Go to GitHub, navigate to the top left corner, click your profile, and select: Settings

Then select "SSH and GPG keys". and click the "New SSH key" button

Select a title, and paste the public SSH key into the "Key" field, and click "Add SSH Key"

You will be prompted to supply your GitHub password.

You will see your new SSH key added:

## Test SSH Connection to GitHub
Now we can test our connection via SSH to GitHub:
```
ssh -T git@github.com
The authenticity of host 'github.com (140.82.121.3)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,140.82.121.3' (RSA) to the list of known hosts.
Hi w3schools-test! You've successfully authenticated, but GitHub does not provide shell access.
```
If the last line contains your username on GitHub, you are successfully authenticated!


## Add New GitHub SSH Remote

Now we can add a new remote via SSH to our Git.

First, get the SSH address from our repository on GitHub

Then use that address to add a new origin:
```
git remote add ssh-origin git@github.com:w3schools-test/hello-world.git
```

### Note: You can change a remote origin from HTTPS to SSH with the command: git remote set-url remote-name git@github.com:username/repository.git

```
git remote set-url origin git@github.com:w3schools-test/hello-world.git
```
