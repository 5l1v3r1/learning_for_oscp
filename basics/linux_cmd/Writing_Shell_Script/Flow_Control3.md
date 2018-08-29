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
	#Only the superuser can get this information
	if [ "$(id -u)" = "0" ]; then
	echo "<h2>Home directory space by user</h2>
	echo "<pre>"
	echo "Bytes Directory"
	du -s 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0NzE1MDM1MiwtMTE5MDU4NDM1NV19
-->