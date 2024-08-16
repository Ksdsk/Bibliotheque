The `git add` command adds a change in the working directory to the [[#Staging Area|staging area]]. It tells [[Git]] that you want to include updates to a particular file in the next commit. However, this command does not really affect the repository in any significant way - changes are not actually recorded until you run [[git commit]].
## How it works
The `git add` and `git commit` commands compose the fundamental Git workflow - They are the means to record versions of a project into the repository's history.

Developing a project revolves around the basic edit/stage/commit pattern:
1. First, you edit your files in the working directory.
2. When you are ready to save a copy of the current state of the project, you stage changes with `git add`.
3. After you're happy with the staged snapshot, you commit it to the project history with `git commit`.
Additionally, if you need to undo a commit or staged snapshot, you can use [[git reset]].
## Staging Area
The primary function of the command is to promote pending changes in the working directory to the *staging area*. The staging area is one of Git's unique feature. Instead of committing all of the changes you've made since the last commit, the stage lets you group related changes into highly focused snapshots before actually committing it tot he project history. As in any revision control system, it's important to create atomic commits so that it's easy to track down bugs and revert changes with minimal impact on the entire project.
## Commands
The generic command is:
```zsh
git add <filename>
```

You can stage all changes recursively for all files in a specific directory:
```zsh
git add <directory>
```

You can stage all changes, for all:
```zsh
git add -A
```

