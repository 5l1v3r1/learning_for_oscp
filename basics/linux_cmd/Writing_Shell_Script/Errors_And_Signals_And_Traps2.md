# Errors And Signals And Traps - Part2
You have to be concerned with signals.

## Cleaning Up After Yourself
A signal can come along and make your script terminate. In some cases it will matter. If the user types ctrl-c after making temporary file and before deleting it, It wont be deleted. So, we need a way to respond to signals such as SIGINT when th Ctrl-c key is typed.

## trap
The **trap** command allows you to execute a command when a signal

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzA1NTM0Mzk5LC02OTYwNzMyMzldfQ==
-->