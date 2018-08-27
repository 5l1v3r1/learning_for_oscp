# Navigation
this document is about first three commands: **pwd** (print working directory), **cd** (change directory), and **ls** (list files and directories).

## File System Organization
Like that legacy operating system, the files are organized in a tree-like pattern of directories. The first directory in the file system is called the **root** directory.

### pwd
The directory you are standing in is called the **working directory**. To find the name of the working directory, use the **pwd** command
```bash
[me@linuxbox me]]$ pwd
/home/me
```
When you first log on to a Linux system, the working directory is set to your home directory. On most systems, your home directory will be called /home/{your_username}

### ls
To list the files in the working directory, use the **ls** command.
```bash
[me@linuxbox me]$ ls
//files and directories in the current directory will be shown here.
```

### cd
To change your working directory (where you are standing) you use the **cd** command. To do this, type cd followed by the passname of the desired working directory.
You can use absolute pathnames.
```bash
[me@linuxbox me]$ cd /usr/bin
[me@linuxbox bin]$ pwd
/usr/bin
```
You can also use relative pathnames.
```bash
[me@linuxbox bin]$ cd ..
[me@linuxbox usr]$ cd bin
[me@linuxbox bin]$ pwd
/usr/bin
```

### A Few Shortcuts
If you type cd followed by nothing, cd will change the working directory to your home directory.
~ means user. So you can use like this
```bash
[me@linuxbox me]$ cd ~/bin
[me@linuxbox me/bin]$ pwd
/home/me/bin
```
```bash
[me@linuxbox me]$ cd ~foo/bin
[me@linuxbox foo/bin]$ pwd
/home/foo/bin
``` 
Typing cd - changes the working direcory to the previous one.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzMDc0NzcyNSwtNTA0MTM5MDI5LDEwOT
A4MjEyOV19
-->