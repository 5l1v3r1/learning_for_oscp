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


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgyNTAzNDI5Nl19
-->