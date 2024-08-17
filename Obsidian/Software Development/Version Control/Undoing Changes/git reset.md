The `git reset` command is a complex and versatile tool for undoing changes in [[Git]].
## How it works
At a surface level, `git reset` is similar in behaviour to [[git checkout]]. Where `git checkout` solely operates on the `HEAD` ref pointer, `git reset` will move the `HEAD` ref pointer and the current branch ref pointer.
### Three Trees
> Three Trees is a Git's internal state management system. Trees are a bit of a misnomer, as they are not strictly traditional tree data-structures. The trees are the [[#Working Directory]], [[#Staging Index]], and [[#Commit History]].
#### Working Directory
This tree is in sync with the local file system and is representative of the *immediate changes* made to the content in files and in directories.
#### Staging Index
This three is tracking the [[#Working Directory]] changes that have been staged with [[git add]], to be stored in the next commit. 
#### Commit History
This tree is a string of permanent snapshots of commits made with [[git commit]].
## Commands
You can use the `--hard` flag to update the ref pointer and the head to the specified commit, then the staging index and working directory are reset to match that of the specified commit. Any previously pending changes to the staging index and the working directory gets reset to match the state of the commit tree; *this means that any pending work that was hanging out in the Staging Index and Working Directory will be lost.*
