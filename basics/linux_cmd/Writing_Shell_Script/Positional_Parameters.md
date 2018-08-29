# Positional Parameters
there are several more features I want to add our script:

1. I want to specify the name of the output file on the command line, as well as set a default output file name if no name is specified.
2. I want to offer an interface mode that will prompt for a file name and warn the user if the file exists and prompt the user to overwrite it.
3. Naturally, we want to have a help option that will display a usage message.

To handle options on the command line, we use a facility in the shell called **positional parameters**. Positional parameters are series of special variables that contain the contents of the command line. 
Let's imagine the following command line:
```bash
[me@linuxbox me]$ some_program word1 word2 word3
```
we could reach each item on the command line because the positional parameters contains the followingl:
- $0 would contain "some_program"
- $1 would contain "word1"
- $2 would contain "word2"
- $3 would contain "word3"

## Detecting Command line arguments
Often, you will want to check to see if you have arguments on which to act. There are a couple of ways to do this. First, you could simply check to see if $1 contains anything. Second, the shell maintains a variable called $# that contains the number of items on the command line in addition to the name of the command ($0).
```bash
#!/bin/bash
if [ $# -gt 0 ]; then
	echo "Your command line contains $# arguments"
else
	echo "Your command line contains no arguments"
fi
```

## Command line options
Now, we will implement -h or --help option.
```bash
interactive=
filename=~/sysinfo_page.html
while [ "$1" != "" ]; do
	case $1 in
		-f | --file ) shift
						 filename=$1
		-i | --interactive ) interactive=1
									  ;;
		-h | --help ) usage
							exit
							;;
		* ) usage
			 exit 1
	esac
	shift
done
```
**shift** is a shell builtin that operates on the positional parameters. It shifts all the positional parameters down by one.

In this script, we have to check the content of *filename* to make sure it is valid.

## Integrating The Command Line Processor Into The script.
We will have to move a few things around and add a usage function to get this new routine in


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4NTkwODI3OF19
-->