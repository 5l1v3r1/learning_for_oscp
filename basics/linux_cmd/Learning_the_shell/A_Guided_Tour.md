# A Guided Tour
For each of the directories listed below, do the following:
- **cd** into each directory
- Use **ls** to list the contents of the directory.
- If you see an interesting file, use the **file** commands to determine its contents.
- For text files, use **less** to view them.

|**Directory**|**Description**|
|:--|:--|
|/|The root directory where the file system begins. In most cases the root directory only contains subdirectories.|
|/boot|This is where the Linux Kernel and boot loader files are kept. The kernel is a file called vmlinux.|
|/etc|The /etc directory contains the configuration files for the system. All of the files in /etc should be text files. Points of interest:
/etc/passwd
	The passwd file contains the essential information for each user. It is here that users are difined.
/etc/fstab
	The fstab file contains a table of device that get mounted when your system boots. This file defines your disk drives.
/etc/hosts/
	This file lists the network host names and IP address that are intrinsically known to the system
/etc/init.d
	This directory contains the script that start various system services typically at boot time.
|/bin, /usr/bin|These two directories contain most of the programs for the system. The /bin directory has the essential programs that the system requires to operate, while /usr/bin contains application for the system's users.|
|:--|:--|
|/sbin, /usr/sbin|The sbin directory contain programs for system administration, mostly for use by the superuser.|
|/usr|The /usr direcotry contains a variety of things that support user applications. Some highlights:
/usr/share/x11
	Support files for the X window system
/usr/share/dict
	Dictionaries for the spelling checker. Bet you didn't know that Linux had a spelling checker. See look and aspell.
/usr/share/doc
	Various documentation files in a varie
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc5MDA4ODQ3NF19
-->