# Git Branch

In Git, a branch is a new/separate version of the main repository.

Let's say you have a large project, and you need to update the design on it.

How would that work without and with Git:

## Without Git:

    * Make copies of all the relevant files to avoid impacting the live version
    * Start working with the design and find that code depend on code in other files, that also need to be changed!
    * Make copies of the dependant files as well. Making sure that every file dependency references the correct file name
    * EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
    * Save all your files, making a note of the names of the copies you were working on
    * Work on the unrelated error and update the code to fix it
    * Go back to the design, and finish the work there
    * Copy the code or rename the files, so the updated design is on the live version
    * (2 weeks later, you realize that the unrelated error was not fixed in the new design version because you copied the files before the fix)

## With Git:

    * With a new branch called new-design, edit the code directly without impacting the main branch
    * EMERGENCY! There is an unrelated error somewhere else in the project that needs to be fixed ASAP!
    * Create a new branch from the main project called small-error-fix
    * Fix the unrelated error and merge the small-error-fix branch with the main branch
    * You go back to the new-design branch, and finish the work there
    * Merge the new-design branch with main (getting alerted to the small error fix that you were missing)
    
Branches allow you to work on different parts of a project without impacting the main branch.

When the work is complete, a branch can be merged with the main project.

You can even switch between branches and work on different projects without them interfering with each other.

Branching in Git is very lightweight and fast!

