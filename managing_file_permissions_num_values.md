# Managing File Permissions using Numeric Values

## What numeric values are assigned to each permission?
- r value is 4
- w value is 2
- x value is 1

They are added together to determine the total permission value for each group.

## What can you do with the values assigned to read + write permissions?
You can add the numbers together to find out the permissions.

## What value would assign read, write and execute permissions?
![num_permissions](/linux_num_permissions.png)

rwx would have a value of 7.

## What value would assign read and execute permissions?
rx would be 5.

## Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?
- The owner has read and write permissions
- The group has read permissions
- Others have read permissions