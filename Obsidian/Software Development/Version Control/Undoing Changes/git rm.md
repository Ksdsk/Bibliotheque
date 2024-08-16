`git rm` is the inverse [[Git]] command of [[git add]], where it aims to convert an individual tracked file into an *untracked file*.
## Commands
Untrack a file from the current working branch with:
```shell
git rm <filename>
```

You can `rm` an entire directory recursively:
```shell
git rm -r <directory-name>
```

You can also undo the `rm` process by [[git reset|git resetting to HEAD]].
