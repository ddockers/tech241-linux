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

# Useful Linux Commands

`ps` command lets you know what processes are running and which shell.

`history` lets you see all commands ever entered in the VM. Can then use `![key number]` to run previous command.

`--help` is the help function.

The root directory in Linux is `/` (like the :C in Windows). You can use `cd` to get directly from root to home. Alternatively, we can enter `cd ~`.

The home directory is `~`

### Navigating files/folders
Get to home directory and root directory. Add instructions.

`ls -la` 
Blue are directories, white are files. Directories have d at the start

`mv` to move or rename a file
Even when renaming a .jpg file to .txt file, linux recognises it's still an image. Use `file` to display file type.
`cp` to copy a file

`rm` to remove a file, `rm -r` to remove a directory and all files it contains.

`mkdir` make directory. You can make multiple directories at the same time by putting a space in between directory name. `mkdir my pics` creates a folder called my and one called pics. `mkdir "my pics"` creates one folder called my pics.

`touch` creates an empty file

Lunix has a built-n next editor called nano. We can create an empty text file and edit it in nano.

`ls -l` gives the long view of a file so you can see permissions.


### Nano
Nano is an in-built text editor. To open nano in Linux, you can follow these steps:

On the command prompt, type `nano` followed by the filename to open the file for editing in Nano.

Use the arrow keys to move the cursor up, down, left and right.

Use Ctrl+A and Ctrl+E to move the cursor to the start and end of the line.

Use Ctrl+Y and Ctrl+V to move the page up and down.

Use Ctrl+X to save and exit the text editor.