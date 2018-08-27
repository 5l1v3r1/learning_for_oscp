# Permissions
This lession will cover the following commands:
- **chmod** - modify file access right
- **su** - temporarily become the superuser
- **sudo** - temporarily become the superuser
- **chown** - change file ownership
- **chgrp** - change a file's group ownership

## File Permission
On a Linux system, each file and directory is assigned access rights for the owner of the file, the members of a group of related users, and everybody else.

To see the permission settings for a file, we can use the **ls** command.
```bash
[me@linuxbox me]$ ls -l /bin/bash

-rwxr-xr-x 1 root root 313334 Feb 27 2000 /bin/bash
```

## chmod
The **chmod** command is used to change the permission of a file or directory. To use it, you specify the desired permission settings and the file or files that you wish to modify.

```bash
[me@linuxbox me]$ chmod 600 bar
```

## Directory Permission
The chmod command can also be used to control the access permission for directories.
- **r** - Allows the contents of the directory to be listed if the x attribute
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ5MzQ4NDE2NSwyOTEzMDQ1NzBdfQ==
-->