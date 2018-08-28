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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcxOTQyMTgzMl19
-->