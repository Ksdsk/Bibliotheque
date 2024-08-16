[[Git]] sees every file in your working copy as one of three things:
- Tracked - a file which has been previously staged or committed;
- Untracked - a file which has not been staged; or
- Ignored - a file which Git has been explicitly told to ignore.

The `.gitignore` file is a standard file that can be created at the root of the repository to tell Git to set files or directories in the ignored state. Usually, the ignored files are:
- Dependency caches, like `/node_modules` or `/packages`,
- Compiled code, such as `.o`, `.pyc`, and `.class` files,
- Build output directories, such as `/bin` and `/out`,
- Files generated at runtime, such as `.log` and `.tmp`,
- Hidden system files, such as `.DS_Store`, or
- Personal IDE config files, like `.idea`.
## Pattern Matching
You can use pattern matching to match against file names:

| Pattern                     | Example Matches                                                                 | Explanation                                                                                                                                                                                                                                                                       |
| --------------------------- | ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `**/logs`                   | `logs/debug.log`<br>`logs/monday/foo.bar`<br>`build/logs/debug.log`             | You can prepend a pattern with a double asterisk (`**`) to match directories anywhere in the repository.                                                                                                                                                                          |
| `**/logs/debug.log`         | `logs/debug.log`<br>`build/logs/debug.log`<br>BUT NOT<br>`logs/build/debug.log` | You can also use a double asterisk to match files based on their name and the name of their parent directory.                                                                                                                                                                     |
| `*.log`                     | `debug.log`<br>`foo.log`<br>`.log`<br>`logs/debug.log`                          | An asterisk (`*`) is a wildcard that matches zero or more characters.                                                                                                                                                                                                             |
| `*.log`<br>`!important.log` | `debug.log`<br>BUT NOT<br>`logs/debug.log`                                      | Prepending an exclamation mark (`!`) to a pattern negates it. If a file matches a pattern, but *also* matches a negating pattern defined later in the file, it will not be ignored.<br><br>Patterns defined after a negating pattern will re-ignore any previously negated files. |
| `/debug.log`                | `debug.log`<br>BUT NOT<br>`logs/debug.log`                                      | Prepending a slash (`/`) matches files only in the repository root.                                                                                                                                                                                                               |
| `debug?.log`                | `debug0.log`<br>`debugg.log`<br>BUT NOT<br>`debug10.log`                        | A question mark (`?`) matches exactly one character.                                                                                                                                                                                                                              |
| ... finish later            |                                                                                 |                                                                                                                                                                                                                                                                                   |
[.gitignore file - ignoring files in Git | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/saving-changes/gitignore#shared)
