### Git rebase, merge 

### Using command line:

 1. Check the git logs using: **git log --oneline --decorate --all --graph**
 2. There is an issue with our feature branch (the commint from which it was created is no longer the latest commit from master! We should do a rebase in order to move our commits on top of the latest master commit):
    - Step 1: Firstly we need to be on the feature branch. Use the checkout command to accomplish this: **git checkout feature/ro-botzi**
    - Step 2: Check the git logs using: **git log --oneline --decorate --all --graph**
    - Step 3: To fix our commit issues use the rebase command: **git rebase master**
 3. Now that we have rebased our changes onto master, the next step is to merge our fetaure branch into it. Do this using the merge command:
    - Step 1: **Pay attention!** We should be on the branch in which we want to merge, to accomplish that we need to move to the master branch. Accomplish this using the: **git checkout master**
    - Step 2: Now that we are on the master branch we can merge our feature branch into it. Accomplish this using the merge command: **git merge feature/ro-botzi**
    - Step 3: Check the git logs using: **git log --oneline --decorate --all --graph**

  4. We skrewd up our commit and it shouldn't have been merged (we freak out), luckily we have yet another git command to help us out. I
    - Step 1: In order to undo the last merge into the master branch use: **git reset HEAD~1**
    - Step 2: We will have the last commit undone but the files still untracked, to remove them use: **git clean -f**
    - Step 3: Let's head over to the ro-botzi branch: **git checkout feature/ro-botzi**
    - Step 4: Do a change in the js file and save it.
    - Step 5: Now that we saved it we should also stage it in order to store it into the git. Use the add command: **git add index.js**
    - Step 6: We have our change staged for commit, the only thing left is to write a message for it, we can accomplish that using the commit command: **git commit -m"change was needed so we have done it!"**

  5. Our branch is now finally ready for merge so:
    - Step 1: Head back into the master branch: **git checkout master**
    - Step 2: **Pay attention!** We now have two commit messages in the feature branch, they are quite ugly and serve no concrete documentation value, we can merge the two commits into a single one that can be more verbose and describe what we have done. We can accomplish this using the merge with the --squash flag: **git merge --squash feature/ro-botzi**
    - Step 3: Now we simply have to provide a new commit message for the squashed commits using: **git commit -m"adds index.js file to serve as an example to the git reabse-merge knowledge sharing"**

### Using VS Code:

> Remove the project directory, and clone the whole project again
> We will repeate the same stepps as before but using Vs Code commands

  - Seeing git logs use: **F1** to open up the Vs Code command interface, search for **Git: View History**.
  - Checking out to another branch use: **F1** to open up the Vs Code command interface, search for **Git: Checkout to...** and select the branch you want to checkout to.
  - Rebasing: Saddly Vs Code doesn't have a Git rebase functionality, we'll use the command line tool.
  - Merging, use:  **F1** to open up the Vs Code command interface, search for **Git: Merge branch...** and select the branch you want to checkout to.
  - Merging interactively is not supported by Vs Code, we need to fallback to command line or a tool like sourcetree.
