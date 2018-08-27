# Manipulating Files
this lesson will introduce you to the following commands:
- **cp** - copy files and directories
- **mv** - move or rename files and directories
- **rm** - remove files and directories
- **mkdir** - create directories

## Wildcards
Special characters to help you rapidly specify groups of filenames is called wildcards.
wildcards allow you to select filenames based on patterns of characters. The table below list the wildcards and what they select:
|**Wildcard**|**Meaning**|
|:--|:--|
|*|Matches any characters|
|?|Matches any single characters|
|[character]|Mathces any character that is a member of the set characters. you can use POSIX character class instead.
	[:alnum:]	Alphanumeric characters
	[:alpha:]	Alphabetic characters
	[:digit:]	Numerals
	[:upper:]	Uppercase
	[:lower:]	Lowercase
|[!characters]|Matches any character that is not a member of the set characters|
|:--|:--|

## cp
The **cp** program copies files and directories. 
```bash
[me@linuxbox me]$ cp file1 file2
```
```bash
[me@linuxbox me]$ cp file... directory
```
if you specified i option and the file you want to make exists, the user is prompted before it is overwritten with the ocntents of original file.

if you want to copy directory, you should specify R option

## mv
the **mv** commands moves or rename files and directories.
```bash
[me@linuxbox me]$ mv filename1 filename2
```
```bash
[me@linuxbox me]$ mv file... directory
```

## rm
The **rm** commands removes (deletes) files and directories.
```bash
[me@linuxbox me]$ rm file...
```
```bash
[me@linuxbox me]$ rm -r directory
```

## mkdir 
The **mkdir** command is used to create directories.
```bash
[me@linuxbox me]$ mkdir directory...
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4Nzg1MDg5MjJdfQ==
-->