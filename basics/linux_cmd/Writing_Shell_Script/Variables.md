# Variables
Now Let's improve our script we made.
```bash
#!/bin/bash

# sysinfo_page - A script to produce an HTML file

title="My System Information"

cat <<- _EOF_
	<html>
	<head>
		<title>
			$title
		</title>
	</head>
	<body>
	<h1>$title</h1>
	</body>
	</html>
_EOF_
```
We added a line to the beginning of the script and replaced the two occurences of the phrase "My System Information" with $title.

## Variables
Variables are areas of memory that can be used to store information and are referred to by a name.

## How to create a variable
To create a variable, put a line in your script that contains the name of the variable followed immediately by an equal sign. After the equal sign, assign the information you wish to store.

## Where Do Variable Names come from?
There are a few rules to choose the names for your variables.

1. Names must start with a letter
2. A name must not contain embedded spaces. Use underscore instead.
3. You cannot use punctuation marks.

## How does this increase Our  Laziness?
First, it will reduce the amount of typing we have to do. and 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMyMjM0MzAxOCwtMjA4ODc0NjYxMl19
-->