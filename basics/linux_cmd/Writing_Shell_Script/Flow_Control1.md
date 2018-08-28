# Flow Control - Part 1
In this lesson, we will look at how to add intelligence to our scripts.
The shell provides several commands that we can use to control the flow of execution in our program. In this lesson, we will look at following:

- if
- test
- exit

## if
It makes a decision based on the exit status of a command. The if command's syntax looks like this:
```bash
if commands; then
commands
[elif commands; then
commands...]
[else
commands]
fi
```

## Exit status
Commands issue a value to the system when they terminate, called an exit status. This value, which is an integer in the range of 0 to 255, indicates the success or failure of the command's execution. By convention, a value of zero indicates success and any other value indicates failure. The shell provides a parameter that we can use to examine the exit status. Here we see it in action:
```bash
ls -d /usr/bin
/usr/bin
echo $?

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3OTkyNjcwMzYsODQ1MzM4OTI4XX0=
-->