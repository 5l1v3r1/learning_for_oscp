# Looking around
you need to know some commands that will come in handy during you learning about linux system. These are:

- **ls** (list files and directories)
- **less** (view text files)
- **file** (classify a file's contents)

## ls
This command is used to list the contents of a directory.

| **Command**|**Result**|
|:--|:--|
|ls|List the files in the working directory|
|ls /bin|List the files in the /bin directory|
|ls -l|List the files in the working directory in long format|
|ls -l /etc/bin|List the files in the /bin directory and the /etc/directory in long format|
|ls -la ..|List all files in the parent of the working directory in long format|
If you use ls with l option, you will get a file listing that contains a wealth of information

- File Name
- Modification Time
- Size
- Group
- Owner
- File Permission

## less  
**less** is a program that lets you view text files. This is very handy since many of the files used to control and configure Linux are human readable.
The less program is invoked by simply typing:
```bash
less text_file
```

### Controlling less
Here are some commands that **less** will accept:

|**Command**|**Action**|
|:--|:--|
|Page up or b|Scroll back one page|
|Page down or space|Scroll forward one page|
|G|Go to the end of the text file|
|1G|Go to the beginning of the text file|
|/character|Search forward in the text file for an occurrence of the specified characters|
|n|Repeat the previous search|
|



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4MzIzNDMwOV19
-->