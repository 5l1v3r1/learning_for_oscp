# Some Real Work
In this lesson, we will develop some of our shell functions and get our script to produce some useful information.

## show_uptime
The show_uptime function will display the output of the **uptime** command. The uptime command outputs several interesting facts about the system.
To get output of the uptime command into our HTML page, we will code our shell functon like this.
```bash
show_uptime()
{
	echo "<h2>System uptime</h2>
	echo "<pre>"
	uptime
	echo "</pre>"
}
```

## drive_space
The drive_space function will use **df** command to provide a summary of the space used by all of the mounted file systems.
In terms of structure, the drive_space function is very similar to the show_uptime function:
```bash
drive_space()
{
	echo "<h2>Filesystem space</h2>"
	echo "<pre>"
	df
	echo "</pre>"
}

## home_space
The home_space function will display the amount of space each 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTA5Mzg4MThdfQ==
-->