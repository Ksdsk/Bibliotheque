The `git revert` command can be considered as an *undo* type of command for [[Git]]. However, it is not a traditional undo operation - instead of removing the commit from the project history, it figures out how to *invert the changes* introduced by the commit and appends a new commit with the resulting inverse content. This prevents Git from losing history. This command is a safer alternative to `git reset` in regards to losing work.

## How it works
The `git revert` command is used for undoing changes to a repository's commit history. It does not move ref