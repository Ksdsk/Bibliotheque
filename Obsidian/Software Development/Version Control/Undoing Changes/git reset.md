The `git reset` command is a complex and versatile tool for undoing changes in [[Git]].
## How it works
At a surface level, `git reset` is similar in behaviour to [[git checkout]]. Where `git checkout` solely operates on the `HEAD` ref pointer, `git reset` will move the `HEAD` ref pointer and the current branch ref pointer.

Because we move both of the pointers to a different node value, it is possible to end up with orphaned commits in history. These orphaned commits can usually be found and restored using [[git reflog]]. However, Git will permanently delete any orphaned commits after it runs the internal garbage collector, which is by default every 30 days.

The safer method to go back to the previous commit is [[git revert]], so first try to see if it's possible to use the `git revert` command before using `git reset` as a final method.
### Three Trees
> Three Trees is a Git's internal state management system. Trees are a bit of a misnomer, as they are not strictly traditional tree data-structures. The trees are the [[#Working Directory]], [[#Staging Index]], and [[#Commit History]].
#### Working Directory
This tree is in sync with the local file system and is representative of the *immediate changes* made to the content in files and in directories.
#### Staging Index
This three is tracking the [[#Working Directory]] changes that have been staged with [[git add]], to be stored in the next commit. 
#### Commit History
This tree is a string of permanent snapshots of commits made with [[git commit]].

## Commands
The `--mixed` flag is a default value for the command, where the staging index is reset to the state of the specified commit:
```shell
git reset
```

You can use the `--hard` flag to update the ref pointer and the head to the specified commit, then the staging index and working directory are reset to match that of the specified commit:
```shell
git reset --hard <commit-id>
```


