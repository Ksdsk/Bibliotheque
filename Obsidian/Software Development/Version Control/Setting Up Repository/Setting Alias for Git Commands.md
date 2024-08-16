It is possible to give an alias for [[Git]] commands. For example, `git checkout` could be aliased to `git co`. There is no direct `git alias` command, but done through using the [[git config]] command.
## Commands
Using the `git config` command:
```shell
git config <configuration level> alias.<alias> <command>

#EXAMPLE
git config --global alias.co checkout
```
