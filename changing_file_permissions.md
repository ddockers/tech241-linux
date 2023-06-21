## What command changes file permissions?
`chmod`, which is short for *change mode*.

## To change permissions on a file what must the end user be? (2 answers)
- The file owner
- A user with sudo privileges - sudo is a command that allows users to run programs with the privileges of another user (the file owner)

## Give examples of some different ways/syntaxes to set permissions on a new file (named testfile.txt) to:
###   Set User to read, Group to read + write + execute, and Other to read and write only
See <https://www.thegeekstuff.com/2010/06/chmod-command-examples/>
- `u` is for user
- `g` is for group
- `o` is for others

- r is read permission
- w is write permission
- x is execute permission

```
chmod u+r, g+rwx, o+rw testfile.txt
```

### Add execute permissions (to all entities)
    chmod a+x testfile.txt

### Take write permissions away from Group
```
chmod g-w testfile.txt
```
## Use numeric values to give read + write access to User, read access to Group, and no access to Other.
See https://www.redhat.com/sysadmin/linux-file-permissions-explained

