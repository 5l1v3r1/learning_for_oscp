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
We will have to move a few things around and add a usage function to get this new routine integrated into our script. We'll also add some test code to verify that the command line processor is working correctly. Our script now looks like this:
```bash
#!/bin/bash

# sysinfo_page - A script to produce a system information HTML file

##### Constants

TITLE="System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

##### Functions

system_info()
{
    echo "<h2>System release info</h2>"
    echo "<p>Function not yet implemented</p>"

}   # end of system_info


show_uptime()
{
    echo "<h2>System uptime</h2>"
    echo "<pre>"
    uptime
    echo "</pre>"

}   # end of show_uptime


drive_space()
{
    echo "<h2>Filesystem space</h2>"
    echo "<pre>"
    df
    echo "</pre>"

}   # end of drive_space


home_space()
{
    # Only the superuser can get this information

    if [ "$(id -u)" = "0" ]; then
        echo "<h2>Home directory space by user</h2>"
        echo "<pre>"
        echo "Bytes Directory"
        du -s /home/* | sort -nr
        echo "</pre>"
    fi

}   # end of home_space


write_page()
{
    cat <<- _EOF_
    <html>
        <head>
        <title>$TITLE</title>
        </head>
        <body>
        <h1>$TITLE</h1>
        <p>$TIME_STAMP</p>
        $(system_info)
        $(show_uptime)
        $(drive_space)
        $(home_space)
        </body>
    </html>
_EOF_

}

usage()
{
    echo "usage: sysinfo_page [[[-f file ] [-i]] | [-h]]"
}


##### Main

interactive=
filename=~/sysinfo_page.html

while [ "$1" != "" ]; do
    case $1 in
        -f | --file )           shift
                                filename=$1
                                ;;
        -i | --interactive )    interactive=1
                                ;;
        -h | --help )           usage
                                exit
                                ;;
        * )                     usage
                                exit 1
    esac
    shift
done

# Test code to verify command line processing

if [ "$interactive" = "1" ]; then
	echo "interactive is on"
else
	echo "interactive is off"
fi
echo "output file = $filename"


# Write page (comment out until testing is complete)

# write_page > $filename
```

## Adding Interactive Mode
The interactive mode is implemented with the following code:
```bash
if [ "$interactive" = "1" ]; then
	response=
	echo -n "Enter name of output file [$filename] > "
	read response
	if [ -n "$response" ]; then
		filename=$response
	fi
	if [ -f $filename ]; then
		echo -n "Output file exists. Overwirte
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMzc1ODQxODkxXX0=
-->