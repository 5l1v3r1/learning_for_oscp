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
	Various documentation files in a variety of formats.
/usr/share/man
	The man pages are kept here.
/usr/src
	Souce code files. If you installed the kernel source code package, you will find the entire Linux kernel source code here.
|/usr/local|/usr/local and its subdirectories are used for the installation of software and other files for use on the local machine. What this really means is that software that is not part of the official distribution (which usually goes in /usr/bin) goes here.

When you find interesting programs to install on your system, they shou.d be installed in one of the /usr/local directories. Most often, directory of choice is /usr/local/bin
|/lib|The shared libraries (similar to DLLs in that other operating system) are kept here.|
|:--|:--|
|/var|The /var directory contains files that changes as the system is running. This includes:
/var/log
	Directory that contains log files
/var/spool
	This directory is used to hold files that are queued for some process, such as mail messages and print jobs.
|/home|/home is where users keep their personal work.|
:--|:--|
|/root|This is the superuser's home directory.
|/tmp|/tmp is a directory in which programs can write their temporary files.|
|/dev|The /dev directory is a special directory, since it does not really contain files in th usual sense. Rather, it contains devices that are available to the system. In Linux (like Unix), devices as though they were files. For example /dev/fd0 is the first floppy disk drive, /dev/sda (/dev/hda on older system) is the first hard drive. All th devices that the kernel understands are represented here.|
|/proc|The /proc directory is also special. This directory does not contain files. In fact, this directory does not really exist at all. It is entirely virtual. The /proc directory contains little peep holes into the kernel itself. There are a group of numbered entries in this directory that correspond to all the processed running on the system. In addition, there are a number of named entries that permit access to the current configuration of the system. Many of these entries can be viewed. /proc/cpuinfo tell you what the kernel thinks of your CPU.|
|/media, /mnt|Finally, we come to /media, a normal directory which is used in a special way. The /media directory is used for mount points. the different physical storage devices are attached to the file system tree in various places. This process of attaching a device to the tree is called **mounting**. For a device to be available, It must first be mounted.

When your system boots, it reads a list of mounting instructions in the file /etc/fstab, which describes which device is mounted at which mount point in the directory tree. This takes care of the hard drives, but you may also have devices that are considered temporary, such as CD-ROMs, thumb derives, and floppy disks. Since these are removable, they do not stay mounted all the time, The /media directory is used by the automatic device mounting mechanisms found in modern desktop oriented Linux distributions. On systems that require manual mounting of removable devices, the /mnt directory provides a convenient place for mounting these temporary devices. You will often see the directories /mnt/floppy and /mnt/cdrom. To see what devices and mount points are used, type **mount**.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDgxMDUyNTE1XX0=
-->