The `git init` command creates a new [[Git]] repository. It can be used to convert an existing, un-versioned project to a Git repository, or initialize a new and empty repository.

## How it works
Executing `git init` creates a `.git` subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository. This metadata includes subdirectories for objects, refs, and template files. A `HEAD` file is also created which points to the currently checked out commit.

By default, `git init` will initialize the Git configuration to the `.git` subdirectory.
### git init vs git clone
At a high level, both `git init` and [[git clone]] is used to create a copy of an existing repository. However, `git clone` is dependent on `git init` - `git clone` is used to create a *copy* of an existing repository which first uses `git init` to create a new repository, then copies data from the existing repository to it.
## Commands
All you have to do is `cd` into the project subdirectory and run `git init` to have a fully functional Git repository.

This command transforms the current directory into a Git repository:
```zsh
git init
```

You can also create an empty Git repository in a specified directory like so:
```zsh
git init <directory>
```
### Bare Repositories
You can initialize an empty Git repository, but omit the working directory. Shared repositories should always be created with the `--bare` flag. This flag creates a repository that doesn't have a working directory, making it impossible to edit files and commit changes in that repository.

> Think of `--bare` as a way to mark a repository as a storage facility, as opposed to a development environment. This means that for virtually all Git workflow, the central repository is *bare*, and developers' local repositories are *non-bare*.

```shell
git init --bare <directory>
```
### Templates
Templates allow you to initialize a new repository with a predefined `.git` subdirectory. You can configure a template to have default directories and files that will get copied to a new repository's `.git` subdirectory.
```shell
git init <directory> --template=<template_directory>
```

