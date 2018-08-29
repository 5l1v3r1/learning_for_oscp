# Errors And Signals And Traps - Part2
You have to be concerned with signals.

## Cleaning Up After Yourself
A signal can come along and make your script terminate. In some cases it will matter. If the user types ctrl-c after making temporary file and before deleting it, It wont be deleted. So, we need a way to respond to signals such as SIGINT when th Ctrl-c key is typed.

## trap
The **trap** command allows you to execute a command when a signal is received by your script. It works like this:
```bash
trap arg signals
```
arg is a command to execute when one of the signals is received.
There is one signal that you cannot trap: SIGKILL or signal 9. The kernel immediately terminates any process sent this signal and no signal handling is performed. Despite its apparent ease, you must remem

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2MjQ3MzI5LC02OTYwNzMyMzldfQ==
-->