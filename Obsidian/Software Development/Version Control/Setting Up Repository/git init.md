The `git init` command creates a new [[Git]] repository. It can be used to convert an existing, un-versioned project to a Git repository, or initialize a new and empty repository.

## How it works
Executing `git init` creates a `.git` subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository. This metadata includes subdirectories for objects, refs, and template files. A `HEAD` file is also created which points to the currently checked out commit.

By default, `git init` will initialize the Git configuration to the `.git` subdirectory.
## Commands
All you have to do is `cd` into the project subdirectory and run `git init` to have a fully functional Git repois