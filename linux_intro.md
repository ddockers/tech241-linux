# Linux

## Why Linux?
- Fast-growing
- Open-source
- Inexpensive
- Stable - can run for a long time without requiring a restart (like Windows)
- Flexible
- Scales well

Linux is made up of the kernel (core OS)

`uname` gives you the os.

`uname --help` gives more information and a list of further commands

`whoami` tells you who the user is

`exit` gets us back to Windows

Linux commands work on Windows in GitBash, but not in Command Prompt.

GitBash is running a version of GNU on top of Windows.

## What is Bash?
Bourne Again SHell
It's an improvement on Unix
A shell is software that provides interface to run commands

## Useful Linux Commands

`ps` command lets you know what processes are running and which shell.

`history` lets you see all commands ever entered in the VM. Can then use `![key number]` to run previous command.

The root directory in Linux is `/`
The home directory is `~`

### Navigating files/folders
Get to home directory and root directory. Add instructions.

`ls -la` 
Blue are directories, white are files. Directories have d at the start

`mv` to move or rename a file
Even when renaming a .jpg file to .txt file, linux recognises it's still an image. Use `file` to display file type.
`cp` to copy a file

`rm` to remove a file

`mkdir` make directory. You can make multiple directories at the same time by putting a space in between directory name. `mkdir my pics` creates a folder called my and one called pics. `mkdir "my pics"` creates one folder called my pics.
