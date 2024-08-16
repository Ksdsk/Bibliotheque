The `git config` command is a convenience function that is used to set [[Git]] configuration values on a global or local project level. These configuration levels correspond to the `.gitconfig` text files. Executing `git config` will modify a configuration text file.
## Configuration Levels
A Git configuration file has different levels:
- `--local`
	- Default value
	- Operates on the context repository the `git config` command gets invoked in.
	- Stored in `.git/config` file of the local repository.
- `--global`
	- Applied to the operating system user.
	- Stored in a file that is located in the user's home directory.
- `--system`
	- Applied across an entire machine.
	- Stored in a `gitconfig` file at the system's root path.
## Commands
Writing a command to set the key and value of the config file is straightforward:
```shell
git config <configuration level> <key> <value>
```
