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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI2ODU3MzU1MCwtMjA4ODc0NjYxMl19
-->