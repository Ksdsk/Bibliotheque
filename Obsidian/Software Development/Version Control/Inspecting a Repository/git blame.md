The `git blame` command is a versatile troubleshooting utility. The high-level function of the [[Git]] command is the display of author metadata attached to specific committed lines in a file. This is used to examine a specific point of a file's history, gets the context as to who the last author was that modified the line, allowing users to explore why the code was added to the repository.

`git blame` is often used with a GUI display, but possible with the CLI interface.

The command only operates on individual files - a filepath is required for any useful output. The default execution will only yield the command's help menu.

### git blame vs git log
While `git blame` displays the last author that modified a line, often times you might want to know when a line was *originally* added. This is where [[git log]] might be more useful. 
## Commands
To use the command, you need a filepath like so:
```shell
git blame <filepath>
```

You can also restrict the output of each lines of the file using the `-L` flag:
```shell
git blame -L <lower-bound>,<upper-bound> <filename>
```

Because whitespace edits are a bit useless, you can suppress any whitespace edits from the blame with the `-w` flag:
```shell
git blame -w <filename>
```

You can also choose to display the commit author's email instead of a name:
```shell
git blame -e <filename>
```
