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
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ1MzM4OTI4XX0=
-->