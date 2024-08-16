`git stash` temporarily *stashes* [[Git]] changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. It can be handy if you need to quickly switch context and work on something else, but you're midway through a code change and aren't quite ready to commit.
## Stashing your work
The `git stash` command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy. 

You can reapply previously stashed changes with `git stash pop`.

However, `git stash` will not stash these by default:
- New files in your working copy that have not yet been staged, and
- Files that have been [[gitignore|ignored]].
## Commands
Basic stash for your staged and unstaged files:
```shell
git stash
```

Re-applying your stashed changes:
```shell
git stash pop
```

Stashing untracked files as an override:
```shell
git stash -u
```

Stashing ignored files (and the untracked files) as an override:
```shell
git stash -a
```

