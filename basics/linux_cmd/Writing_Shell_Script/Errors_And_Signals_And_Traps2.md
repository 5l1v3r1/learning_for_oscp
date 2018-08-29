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
There is one signal that you cannot trap: SIGKILL or signal 9. The kernel immediately terminates any process sent this signal and no signal handling is performed. Despite its apparent ease, you must remember that when you send this signal, no processing is done by the application.
Be warned. Use SIGKILL as a last resort.

## A clean_up Function
You had better create function in which multiple commands you want to execute when program is finished and pass it arg of the trap command.

## Create Safe Temporary Files
You have to create temporary files in your home directory. A good file name will help you figure out what wrote the file, but will not be entirely predictable.
you can choose good file name like this:
`printfile(program_name).$$(pid).$random(random_number)`

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NTIzNjY0MTIsLTY5NjA3MzIzOV19
-->