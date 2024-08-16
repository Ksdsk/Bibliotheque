The `git commit` command captures a snapshot of the project's currently staged changes. Committed snapshots are regarded as a "safe" version of a project - [[Git]] will never change them unless the developer explicitly asks it to.
## How it works
At a high-level, Git can be thought of as a timeline management utility. Commits, in this analogy, would be the core building block units of a Git project timeline - a milestone or a snapshot of the current project. You can decide what changes to store within each commit by using the [[git add]] command. Commits are created with the `git commit` command to capture the state of a project at that point in time. All the accumulated commits are first stored locally until the developer [[git push|pushes]] the commits to the central repository.

Because storing the history of every directories of a project would be massively difficult and unscalable, Git's version control model works based on these snapshots. Unlike other tools like [[SVN]] which stores the differences of each version, or the *diffs*, which is useful for building a project to the current timeline from scratch, snapshots are much, much faster.

> Snapshot to a repository is like a *screenshot to a video*.

Although these snapshots are not human-readable, developers can choose to add a commit message which can be a useful tool to remind what this snapshot was about upon committing.
## Commands
Most commonly, you can create a current snapshot of your repository simply with:
```shell
git commit
```

To commit a snapshot of all changes in the working directory:
```shell
git commit -a
```

You can add the commit message with the `-m` flag:
```shell
git commit -m "<commit-mesage>"
```

You can add the current changes to the last commit by adding the `--amend` flag:
```shell
git commit --amend
```
