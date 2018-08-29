# Errors and signals and traps - part1
In this lesson, we're going to look at handling errors during the execution of your scripts.
The difference between a good program and a poor one is often measured in terms of the program's robustness. That is, the program's ability to handle situations in which something goes wrong.

## Exit status
It is very important to check the exit status of programs you call in your scripts. It is also important that your scripts return a meaningful exit status when they finish.

## Checking the exit status
You can examine the contents of the $? environment variable to get and respond to the exit status of a program. It will contain the exit status of the last command executed.

## An Error Exit Function
It makes sense to write a function that will display error message. This will save more typing and promote laziness.
```bash
error_exit()
{
	echo "$1" 1>&2
	exit 1
}

if cd $some_directory; then
	rm *
else
	error_exit "Cannot change directory! Aborting."
fi
```

## AND And OR List
You can simplify our script by using the AND and OR control operators.
`command1 && command2`
command2 is executed if, and only if, command1 returns an exit status of zero.
`command1 || command2`
command2 is executed if, and only if, command1 returns a non-zero exit status.

Using this technique, we can write an even simpler version
```bash
cd $some_directory || error_exit "Cannot change directory! Aborting"
rm *
```

## Improving The Error Exit Function
You had better include the name of the program in the error message to make clear where the error is coming from. Also, note the inclusion of the LINENO environment variable which will help you identify the exact line within your script where the error occurred.
```bash
#!/bin/bash
#A slicker error handling routine

#I put a variable in my scripts named PROGNAME which
#holds the name of the program being run. You can get this
#value from the first item on the command line

PROGNAME=$(basename $0)

error_exit()
{
	echo "${PROGNAME}: $(1:-"Unknown Error"}" 1>&2
	exit 1
}

echo "Example of error with line number and message"
error_exit "$LINENO: An Error has occurred."
```

You can surround a variable name with curly braces. ${1:-"Unknown Error"} means that if parameter 1($1) is undefined, substitute the string "Unknown Error" in its 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA2Mjc3ODA2MSwtMjA4ODc0NjYxMl19
-->