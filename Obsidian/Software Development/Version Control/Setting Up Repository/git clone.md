`git clone` is a [[Git]] command which is used to target an existing repository and create a *clone*, or a copy of the target repository. If a project has already ben set up in a central repository, the `git clone` command is the most common way for users to obtain a development copy.

Like [[git init]], cloning is generally a cone-time operation. Once a developer has obtained a working copy, all version control operations and collaborations are managed through their local repository.
## How it works
The `git clone` command copies an existing Git repository by first running `git init` on the target subdirectory, then copies all of the current files into the initialized directory. As a convenience, cloning automatically creates a remote connection called *origin*, which points back to the original repository, making it very easy to interact with a central repository.
## Commands
You can clone a repository directly from the web using different [[Network Protocols]] like **HTTPS** and **SSH**. In either case, the command will be very akin to the following:
```shell
git clone <repository>
```

You can clone the above to a specific folder:
```shell
git clone <repository> <directory>
```

You can close a specific reference point of the repository:
```shell
git clone --branch <tag> <repo>
```

You can also create a **shallow clone** of your repository, which only clones the history of commits specified by the option `depth`. For example, `depth=1` will only clone the latest commit:
```shell
git clone -depth=1 <repo>
```

You can clone a specific branch of the repository instead of the branch the remote `HEAD` is pointing to (usually the `main` branch):
```shell
git clone --branch
```

You can also create a *bare* clone of the repository, which doesn't have a working directory (you cannot edit anything, but only pull and push):
```shell
git clone --bare
```
