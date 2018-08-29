# Flow Control - Part 3
Now, it is time to cover the remaining flow control statement, **for**. for works like this:
```bash
for variable in words; do
	commands
done
```
```bash
#!/bin/bash

for i in word1 word2 word3; do
	echo $i
done
```
we can construct the list of words using command substitution, all kinds of expansions.
```bash
#!/bin/bash

count=0
for i in $(cat ~/.bash_profile); do
	count=$((count + 1))
	echo "Word $count ($i) contains $(echo -n $i | wc -c) characters"
done
```
So what's this got to do with positional parameters? Well, one of the features of **for** is that it can use the positional parameters as the list of words:
```bash
#!/bin/bash

for i in "$@"; do
	echo $i
done
```
The shell variables "$@" contains the list of command line arguments. This technique is often used to process a list of files on the command line. Here is another example:
```bash
#!/bin/bash

for filename in "$@"; do
	result=
	if [ -f "$filename" ]; then
		result="$filename is a regular file"
	else
		if [ -d "$filename" ]; then
			result="$filename is a directory"
		fi
	fi
	if [ -w "$filename" ]; then
		result="$result and it is writable"
	else
		result="$result and it is not writable"
	fi
	echo "$result"
done
```
Here is another example script. This one compares the files in two directories and lists which files in the first directory are missing from the second.
```bash
#!/bin/bash

#cmp_dir - program to compare two directories
#check for required arguments
if [ $# -ne 2 ]; then
	echo "usage: $0 directory_1 directory_2" 1>&2
	exit 1
fi

#Make sure both arguments are directories
if [ ! -d $1 ]; then
	echo "$1 is not a directory!" 1>&2
	exit 1
fi
if [ ! -d $2 ]; then
	echo "$2 is not a directory!" 1>&2
	exit 1
fi

#Process each file in directtory_1, comparing it to directory_2
missing=0
for filename in $1/*; do
	fn=$(basename "$filename")
	if [ -f "$filename" ]; then
		if [ ! -f "$2/$fn" ]; then
			echo "$fn is missing from $2"
			missing=$((missing + 1))
		fi
	fi
done
```
We are going to improve the *home_space* function in our script to output more information.
```bash
home_space()
{
	echo "<h2>Home directory space by user</h2>"
	echo "<pre>"
	format="%8s%10s%10s	%-s\n"
	printf "$format" "Dirs" "Files" "Blocks" "Directory"
	printf "$format" "----" "-----" "------" "---------"
	if [ $(id -u) = "0" ]; then
		dir_list="/home/*"
	else
		dir_list=$HOME
	fi
	for home_dir in $dir_list; do
		total_dirs=$(find $home_dir -type d | wc -l)
		total_files=$(find $home_dir -type f | wc -l)
		total_blocks=$(du -s $home_dir)
		printf "$format" $total_dirs $total_files $total_blocks
	done
	echo "</pre>"
}
```
This improved version introduces a new command **printf**, which is used to produce formatted output according to the contents of a format string.
We also introduce the **find** command. find is used to search for files or directories that meet specific criteria. In the *home_space* function, we use find to list the directories and regular files in each home directory. Using the wc command, we count the number of files and directories found.

Another function that can use a **for** loop is our unfinished *system_info* function. We can build it like this:
```bash
system_info()
{
	if ls /etc/*release 1>/dev/null 2>&1; then
		echo "<h2>System release info</h2>"
		echo "<pre>"
		for i in /etc/*release; do
			head -n 1 $i
		done
		uname -orp
		echo "</pre>"
	fi
}
```
We use the **uname** command with the "o", "r", "p", options to obtain some additional information from the system.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NzU4Mzk1LC0zOTY4MjkzMTYsLTExOT
A1ODQzNTVdfQ==
-->