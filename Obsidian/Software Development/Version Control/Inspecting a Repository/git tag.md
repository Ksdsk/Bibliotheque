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
git tag -a <tag-n
```