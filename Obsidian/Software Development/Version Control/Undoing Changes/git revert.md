The `git revert` command can be considered as an *undo* type of command for [[Git]]. However, it is not a traditional undo operation - instead of removing the commit from the project history, it figures out how to *invert the changes* introduced by the commit and appends a new commit with the resulting inverse content. This prevents Git from losing history. This command is a safer alternative to [[git reset]] in regards to losing work.

## How it works
The `git revert` command is used for undoing changes to a repository's commit history. It does not move ref pointers to the specific commit, but inverse the changes from that commit, and create a new "revert commit". 
### Resetting vs reverting
it's important to understand that `git revert` undoes a single commit through the inverse operation of the specified commit. `git reset` actually moves the `HEAD` backwards to the previous commit and deletes the commit within that process. 
## Commands
You can run the following to create and edit the commit message prior to committing the revert:
```shell
git revert <commit-id>
```
