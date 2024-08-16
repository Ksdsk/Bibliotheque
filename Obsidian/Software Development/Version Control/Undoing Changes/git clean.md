`git clean` is a convenience method for deleting untracked files in a [[Git]] repository's working directory. Overall, the effect of the command can be accomplished using the [[git status]] and the operating system's native deletion tools. `git clean` can also be used alongside [[git reset]] to fully undo any [[git add|additions]] or [[git commit|commits]] in a repository.
## Commands
You can run a simple cleaning process using the following:
```shell
git clean
```

You can also target an entire untracked directory using the `-d` flag:
```shell
git clean -d
```
