The `git add` command adds a change in the working directory to the staging area. It tells [[Git]] that you want to include updates to a particular file in the next commit. However, this command does not really affect the repository in any significant way - changes are not actually recorded until you run [[git commit]].
## How it works
The `git add` and `git commit` commands compose the fundamental Git workflow - They are the means to record versions of a project into the repository's history.

Developing a project revolves around the basic edit/stage/commit pattern:
1. First, you edit your files in the working directory.
2. When you are 