# Here Scripts
Beginning with this lesson, we will construct a useful application. This application will produce an HTML document that contains information about your system. As we construct our script, we will discover step by step the tools needed to solve the problem at hand.

## Writing An HTML File With A Script
With we already know, we could write a script to produce the HTML content:
```bash
#!/bin/bash

# sysinfo_page - A script to produce an html file

echo "<html>"
echo "<head>"
echo "    <title>"
echo "    The title of your page"
echo "</head>"
echo ""
echo "<body>"
echo "    Your page content goes here."
echo "</body>"
echo "</html>"
```
This script can be used as follows:
```bash
[me@linuxbox me]$ sysinfo_page > sysinfo_page.html
```

The first improvement to this script will be to replace the repeated use of the **echo** command with a single instance by using quotation more efficiently:
````bash
#!/bin/bash

# sysinfo_pa
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU1MzY3OTYwMiwzODMxODIzMzFdfQ==
-->