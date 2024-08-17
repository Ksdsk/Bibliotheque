The `git rebase` command is a [[Git]] utility that specializes in integrating changes from one branch onto another along with [[git merge]].

In Git, *rebasing* is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow:

![[Pasted image 20240816232059.png]]
[git rebase | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)

From a content perspective, rebasing is changing the base of your branch from one commit to another, making it appear as if you'd created your branch from a different commit. Internally, Git does this by creating new commits and applying them to the specified base. 

The reason why we may want to use `git rebase` is to maintain a linear project history.
## Commands
To use the interactive rebase mode:
```shell
git rebase -i <base>
```
... where the `<base>` can be a commit ID, a branch name, or a relative reference to `HEAD`.
