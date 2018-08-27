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
|h|Display a complete list less commands and options|
|q|Quit|

## file
It is helpful to determine what kind of data a file contains before you try to view it.
To use the **file** program, just type:
```bash
file name_of_file
```

The **file** program can recognize most type of files, such as:
|**File Type**|**Description**|**Viewable as text**|
|:--|:--|:--|
|Ascii text|The name says it all|yes|
|Bounce-Again shell script|A bash script|yes|
|ELF 32-bit LSB core file|A core dump file(a program will create this when it crashes)|no|
|ELF 32-bit LSB shared object|A shared library|no|
|GNU tar archive|A tape archive file. A common way of storing groups of files.|no, use  tar tvf  to view listing.|
|ELF 32-bit LSB executable|An executable binary program|no|
|gzip compressed data|An archive compressed with gzip|no|
|HTML document text|A web page|yes|
|JPEG image data|A compressed JPEG image|no|
|PostScript document text|A PostScript file|yes|
|RPM|A Red Hat Package Manager archive|no, use  rpm -q  to examine contents.|
|Zip archive data|An archive compressed with  zip|no|


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4OTUwNjY4MzhdfQ==
-->