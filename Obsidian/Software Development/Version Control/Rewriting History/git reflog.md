[[Git]] keeps track of updates to the tip of branches using a mechanism called reference logs, or *reflogs*. Many Git commands accept a parameter for specifying a reference to a commit, like `git checkout`, `git reset`, or `git merge`.

These reflogs track when Git refs were updated in the local repository. In addition to the branch tip reflogs, a special reflog is maintained for the [[git stash]]. 

These reflogs are stored in directories under the local repository's `.git` directory - `.git/logs/...`.
## Commands
Output the log of a ref with:
```shell
git reflog show <ref>
```

You can get a complete reflog of ALL REFs:
```shell
git reflog show --all
```

...as well as for all of your stash:
```shell
git reflog stash
```

