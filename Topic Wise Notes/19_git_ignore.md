# Git Ignore and .gitignore

## Git Ignore
When sharing your code with others, there are often files or parts of your project, you do not want to share.

Examples

* log files
* temporary files
* hidden files
* personal files
* etc.

Git can specify which files or parts of your project should be ignored by Git using a `.gitignore` file.

Git will not track files and folders specified in `.gitignore`. However, the `.gitignore` file itself IS tracked by Git.

## Create .gitignore

To create a `.gitignore` file, go to the root of your local Git, and create it:
```
touch .gitignore
```

Now open the file using a text editor.

We are just going to add two simple rules:

* Ignore any files with the `.log` extension
* Ignore everything in any directory named `temp`

```
# ignore ALL .log files
*.log

# ignore ALL files in ANY directory named temp
temp/
```
Now all `.log` files and anything in `temp` folders will be ignored by Git.

### Note: In this case, we use a single `.gitignore` which applies to the entire repository.It is also possible to have additional `.gitignore` files in subdirectories. These only apply to files or folders within that directory.

## Rules for .gitignore
Here are the general rules for matching patterns in `.gitignore` files: 

| Pattern                | Explanation/Matches                                   | Examples                  |
| :--------------------: | :---------------------------------------------------: | :-----------------------: |
|                        | Blank lines are ignored                               |                            |
| `# text comment`       | Lines starting with # are ignored                     |                            |
| name                   | All name files, name folders, and files and folders   | /name.log                 |
|                        | in any `name` folder                                  | /name/file.txt            |
|                        |                                                       | /lib/name.log             |
| name/                  | Ending with `/` specifies the pattern is for a folder.| /name/file.txt            |
|                        | Matches all files and folders in any `name` folder    | /name/log/name.log        |
|                        | No match: `/name.log`                                 |                            |
| name.file              | All files with the name `name.file`                   | /name.file                |
|                        |                                                       | /lib/name.file            |
| /name.file             | Starting with `/` specifies the pattern matches only  | /name.file                |
|                        | files in the root folder                              | No match: /lib/name.file  |
| lib/name.file          | Patterns specifying files in specific folders are     | /lib/name.file            |
|                        | always relative to root (even if you don't start with `/`)| No match: name.file      |
|                        |                                                       | /test/lib/name.file       |
| **/lib/name.file       | Starting with `**/` specifies it matches any folder   | /lib/name.file            |
|                        | in the repository, not just the root                  | /test/lib/name.file       |
| **/name                | All `name` folders, and files and folders in any      | /name/log.file            |
|                        | `name` folder                                         | /lib/name/log.file        |
|                        |                                                       | /name/lib/log.file        |
| /lib/**/name           | All `name` folders, and files and folders in any      | /lib/name/log.file        |
|                        | `name` folder within the `lib` folder                 | /lib/test/name/log.file   |
|                        |                                                       | /lib/test/ver1/name/log.file|
|                        | No match: /name/log.file                              |                            |
| *.file                 | All files with `.file` extension                      | /name.file                |
|                        |                                                       | /lib/name.file            |
| *name/                 | All folders ending with `name`                        | /lastname/log.file        |
|                        |                                                       | /firstname/log.file       |
| name?.file             | `?` matches a single non-specific character           | /names.file               |
|                        |                                                       | /name1.file               |
|                        | No match: /names1.file                                |                            |
| name[a-z].file         | `[range]` matches a single character in the specified | /names.file               |
|                        | range (in this case a-z, can be numeric as well)      | /nameb.file               |
|                        | No match: /name1.file                                 |                            |
| name[abc].file         | `[set]` matches a single character in the set of      | /namea.file               |
|                        | characters (in this case either a, b, or c)           | /nameb.file               |
|                        | No match: /names.file                                 |                            |
| name[!abc].file        | `[!set]` matches a single character except the ones   | /names.file               |
|                        | specified in the set of characters (in this case a, b,| /namex.file               |
|                        | or c)                                                 | No match: /namesb.file    |
| *.file                 | All files with `.file` extension                      | /name.file                |
|                        |                                                       | /lib/name.file            |
| name/                  |                                                       |                            |
| !name/secret.log       | `!` specifies a negation or exception. Matches all    | /name/file.txt            |
|                        | files and folders in any `name` folder, except        | /name/log/name.log        |
|                        | `name/secret.log`                                     | No match: /name/secret.log|
| *.file                 | All files with `.file` extension                      | /log.file                 |
| !name.file             | `!` specifies a negation or exception. All files with | /lastname.file            |
|                        | `.file` extension, except `name.file`                 | No match: /name.file      |
| *.file                 | All files with `.file` extension                      | /log.file                 |
| !name/*.file           | Adding new patterns after a negation will re-ignore a | /name/log.file            |
| junk.*                 | previously negated file. All files with `.file`       | /log.file                 |
|                        | extension, except the ones in the `name` folder.      | No match: /name/junk.file |
|                        | Unless the file name is `junk.*`                      |                            |

## Local and Personal Git Ignore Rules

It is also possible to ignore files or folders but not show it in the distributed `.gitignore` file.

These kinds of ignores are specified in the `.git/info/exclude` file. It works the same way as `.gitignore` but are not shown to anyone else.