# Managing File Ownership

## Why is managing file ownership important?
- It allows the owner to control who accesses files
- It prevents unauthrised access
- Files with sensitive information can be restricted to specific users

## What is the command to view file ownership?
`ls -l` displays file permissions and ownership.

## What permissions are set when a user creates a file or directory? Who does file or directory belong to?
### Creating a file
- The file belongs to the user's primary group
- The default permissions are 644 - the owner has rw permissions, everyone else has r permissions.

### Creating a directory
  - The directory belongs to the user's primary group
  - The default permissions are 755 - the owner has rwx permissions, everyone else has x permissions

## Why does the owner, by default, not receive X permissions when they create a file?
The reason why the owner, by default, does not receive execute permissions when they create a file is for security reasons. If the owner of a file has execute permissions, it means that they can run the file as a program. This can be dangerous if the file contains malicious code or if the owner accidentally runs the wrong file.

## What command is used to change the owner of a file or directory?
`chown` can be used to change the owner of a file or directory.
```
chown user file.txt
```

# Managing File Permissions
## Does being the owner of a file mean you have full permissions on that file?
Being the owner means you have rw permissions, not x permissions.

## If you give permissions to the User entity, what does this mean?
If you give permissions to the User entity, it means that the user who owns the file has those permissions. The user entity is represented by the owner of the file.

For example, if you give read and write permissions to the user entity on a file named `file.txt`, it means that the owner of the file has read and write permissions on that file.


## If you give permissions to the Group entity, what does this mean?
If you give permissions to the Group entity, it means that all members of the group that owns the file have those permissions. The group entity is represented by the group that owns the file


## If you give permissions to the Other entity, what does this mean
If you give permissions to the Other entity, it means that all users who are not the owner of the file and not members of the group that owns the file have those permissions.

### You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file?
I (the user) will have only r permissions 

###H ere is one line from the `ls -l`. Work everything you can about permissions on this file or directory.
```
-rwxr-xr-- 1 tcboony staff  123 Nov 25 18:36 keeprunning.sh
```
- The permissions are represented by ten characters, which are divided into three groups of three characters each
- The first group represents the permissions for the owner of the file, the second group represents the permissions for g that owns the file, and the third group represents the permissions for o
  
  The owner has rxw permissions. the group has rx permissions and others have r permissions.

**Further explanation**
*The first character in each group represents read permission, the second character represents write permission, and the third character represents execute permission. If a character is replaced by a `-`, it means that permission is not granted.*

*For example, if you see `-rw-r--r--` in the output of `ls -l`, it means that the owner has read and write permissions, but not execute permissions; members of the group that owns the file have read permissions only; and all other users have read permissions only.*