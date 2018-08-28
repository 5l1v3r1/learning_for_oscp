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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1ODQwNjY4MCwtMjA4ODc0NjYxMl19
-->