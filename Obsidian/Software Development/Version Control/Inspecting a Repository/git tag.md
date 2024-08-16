Tagging in [[Git]] is generally used to capture a point in history that is used for a marked version release (i.e. v1.0.1). Treat tags like a [[git branch]] that doesn't change. Unlike branches, tags, after being created, have no further history of commits. 
## Commands
To create a new tag, execute the following:
```shell
git tag <tag-name>
```
... where the `<tag-name>` is usually a semantic identifier to the state of the repo at the time the tag is being created. A common pattern is to use version numbers like `v1.2`. 

You can also create an *annotated tag*, which stores a lot more metadata:
```shell
git tag -a <tag-name>
```

For example, for an annotated tag you can add a tag message:
```shell
git tag -a <tag-name> -m <tag-message>
```

You can view the list of stored tags in a repository:
```shell
git tag
```

You can refine the list of tags with the `-l` option:
```shell
git tag -l <pattern-to-match>
```

You can push a tag to remote, which has to be done explicitly:
```shell
git push origin <tag-name>
```

You can also [[git checkout|checkout]] a tag:
```shell
git checkout <tag-name>
```

You can delete tags:
```shell
git tag -d <tag-name>
```


