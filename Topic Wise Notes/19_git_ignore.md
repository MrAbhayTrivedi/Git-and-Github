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

|Pattern	             Explanation/Matches	                Examples    
|                        Blank lines are ignored	 
|`# text comment`	     Lines starting with # are ignored 
|
|name	                 All name files, name folders,       /name.log
|                        and files and folders in            /name/file.txt
|                        any name folder	                    /lib/name.log
|
|name/	                 Ending with / specifies the         /name/file.txt
|                        pattern is for a folder.            /name/log/name.log
|                        Matches all files and folders       no match:
|                        in any name folder                  /name.log
|
|name.file	            All files with the name.file	    /name.file
|                                                            /lib/name.file
|
|/name.file	            Starting with / specifies the       /name.file
|                        pattern matches only files in       no match:
|                        the root folder                     /lib/name.file
|
|lib/name.file	        Patterns specifiing files in        /lib/name.file
|                        specific folders are always         no match:
|                        realative to root (even if          name.file
|                        you do not start with / )           /test/lib/name.file
|
|**/lib/name.file	    Starting with ** before /           /lib/name.file
|                        specifies that it matches           /test/lib/name.file
|                        any folder in the repository. 
|                        Not just on root.
|
|**/name	                All name folders, and files         /name/log.file
|                        and folders in any name folder	    /lib/name/log.file
|                                                            /name/lib/log.file
|
|/lib/**/name	        All name folders, and files and     /lib/name/log.file
|                        folders in any name folder within   /lib/test/name/log.file
|                        the lib folder.                     /lib/test/ver1/name/log.file
|                                                            no match:
|                                                            /name/log.file
|
|*.file	                All files withe .file extention 	/name.file
|                                                            /lib/name.file
|
|*name/	                All folders ending with name	    /lastname/log.file
|                                                            /firstname/log.file
|
|name?.file	            ? matches a single non-specific     /names.file
|                        character	                        /name1.file
|                                                            no match:
|                                                            /names1.file
|
|name[a-z].file	        [range] matches a single character  /names.file
|                        in the specified range (in this     /nameb.file
|                        case a character in the range       no match:
|                        of a-z, and also be numberic.)	    /name1.file
|
|name[abc].file	        [set] matches a single character    /namea.file
|                        in the specified set of characters  /nameb.file
|                        (in this case either a, b, or c)	no match:
|                                                            /names.file
|
|name[!abc].file	        [!set] matches a single character,  /names.file
|                        except the ones spesified in the    /namex.file
|                        set of characters (in this case     no match:
|                         a, b, or c)	                    /namesb.file
|
|*.file	                All files withe .file extention	    /name.file
|                                                            /lib/name.file
|
|name/
|!name/secret.log	    ! specifies a negation or           /name/file.txt
|                        exception. Matches all files        /name/log/name.log
|                        and folders in any name folder,     no match:
|                        except name/secret.log              /name/secret.log
|
|*.file
|!name.file	            ! specifies a negation or           /log.file
|                        exception. All files withe          /lastname.file
|                        .file extention, except name.file	no match:
|                                                            /name.file
|
|*.file
|!name/*.file
|junk.*	                Adding new patterns after a         /log.file
|                        negation will re-ignore a previous  /name/log.file
|                        negated file                        no match:
|                        All files withe .file extention,    /name/junk.file
|                        except the ones in name folder. 
|                        Unless the file name is junk
|
## Local and Personal Git Ignore Rules

It is also possible to ignore files or folders but not show it in the distributed `.gitignore` file.

These kinds of ignores are specified in the `.git/info/exclude` file. It works the same way as `.gitignore` but are not shown to anyone else.