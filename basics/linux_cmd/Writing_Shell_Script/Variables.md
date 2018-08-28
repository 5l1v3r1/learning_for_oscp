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
To create a variable, put a line in your script that contains the name of the variable followed immediately 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3NTc1Nzc1NSwtMjA4ODc0NjYxMl19
-->