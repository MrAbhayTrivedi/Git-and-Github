# Git Security SSH

## Git Security
HTTPS will usually work just fine, but you should use SSH if you work with unsecured networks. And sometimes, a project will require that you use SSH.

## What is SSH
* SSH is a secure shell network protocol that is used for network management, remote file transfer, and remote system access.

* SSH uses a pair of SSH keys to establish an authenticated and encrypted secure network protocol. It allows for secure remote communication on unsecured open networks.

* SSH keys are used to initiate a secure "handshake". When generating a set of keys, you will generate a "public" and "private" key.

* The "public" key is the one you share with the remote party. Think of this more as the lock.

* The "private" key is the one you keep for yourself in a secure place. Think of this as the key to the lock.

* SSH keys are generated through a security algorithm. It is all very complicated, but it uses prime numbers, and large random numbers to make the public and private key.

* It is created so that the public key can be derived from the private key, but not the other way around.

## Generating an SSH Key Pair

In the command line for Linux, Apple, and in the Git Bash for Windows, you can generate an SSH key.

Let's go through it, step by step.

Start by creating a new key, using your email as a label:
```
ssh-keygen -t rsa -b 4096 -C "yourmail@gmail.com"
```
You will be prompted with the following through this creation:
```
Enter file in which to save the key (/c/Users/user/.ssh/id_rsa):
```
Select a file location, or press "Enter" to use the default file location.
```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
Entering a secure passphrase will create an additional layer of security. Preventing anyone who gains access to the computer to use that key without the passphrase. However, it will require you to supply the passphrase anytime the SSH key is used.

Now we add this SSH key pair to the SSH-Agent (using the file location from above):

```
ssh-add /Users/user/.ssh/id_rsa
Enter passphrase for /Users/user/.ssh/id_rsa:
Identity added: /Users/user/.ssh/id_rsa (yourmail@gmail.com)
```
You will be prompted to supply the passphrase, if you added one.

Now the SSH key pair is ready to use.