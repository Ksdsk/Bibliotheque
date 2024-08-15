`git clone` is a [[Git]] command which is used to target an existing repository and create a *clone*, or a copy of the target repository. If a project has already ben set up in a central repository, the `git clone` command is the most common way for users to obtain a development copy.

Like [[git init]], cloning is generally a cone-time operation. Once a developer has obtained a working copy, all version control operations and collaborations are managed through their local repository.
## How it works
The `git clone` command copies an existing Git repository by first running `git init` on the target subdirectory, then copies all of the current files into the initialized directory. As a convenience, cloning automatically creates a remote connection called *origin*, which points back to the original repository, making it very easy to interact with a central repository.
## Commands
You can clone a repository directly from the web (HTTPS) 