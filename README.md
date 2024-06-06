# Checkout a clean copy into a temporary directory

This command lets you checkout a clean copy of a repository into a temporary directory. It is useful when you want to test something without either affecting the current working directory or being affected by the ignored files in the current working directory.

Example:

```bash
~/Projects/git-tmp$ git tmp
Preparing worktree (detached HEAD 4750c17)
HEAD is now at 4750c17 init
You are now at: /tmp/tmpwih1dkjq
This directory will be removed if not changed when exiting this shell.
/tmp/tmpwih1dkjq$ # you are now in a clean copy of the repository
/tmp/tmpwih1dkjq$ exit
~/Projects/git-tmp$
```

## Installation

Copy the `git-tmp` script to somewhere in your `$PATH`.

## How it works

The `git-tmp` script creates a temporary directory and makes it a [working tree](https://git-scm.com/docs/git-worktree) of current git repository. Then it spawns a shell in this directory.

Working trees created in this way will contain an extra file `.git` which points to the original repository. The script will remove this file to make sure the temporary directory only contains committed files.

After the shell exits, it tries to remove this working tree only if the content has not been changed.

## Disclaimer

This script is not tested with all possible edge cases. Use at your own risk. It should be very safe though.
