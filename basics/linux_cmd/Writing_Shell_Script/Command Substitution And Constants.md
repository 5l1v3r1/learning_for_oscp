# Command Substitution and Constants
Now, we will add a timestamp to the page to indicate when it was last updated.
add`<p>Updated on $(date +"%x %r %Z") by $USER</p>` below the h1 tag.

The characters "$()" tell the shell, "substitute the results of the enclosed command." 
The *date* command has many features and formatting options. To look at them all, try this:
```bash
[me@linuxbox me]$ date --help | less
```

## Assigning A Command's Result To A Variable
You can also assign the results of a command to a variable:
```bash
right_now=$(date +"%x %r %Z")
```
You can even nest the variables (place one inside another), like this:
```bash
right_now=$(date +"%x %r %Z")
time_stamp="Updated on $right_now by $USER"

## Constants
values that, once set, should never be changed is called **constants**. If a value is intended to be a constant, it is given an uppercase name to remind the programmer that it should be considered a constant.

So with everything we know, our program looks like this:
```bash
#!/bin/bash

# sysinfo_page - A script to produce an HTML file

title="System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

cat <<- _EOF_
	<html>
	<head>
		<title>
		$title
		</title>
	</head>
	<body>
		<h1
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzcwNjI2NiwtNDEwMDM0NTExXX0=
-->