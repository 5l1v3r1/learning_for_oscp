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
0
ls -d /bin/usr
ls: cannot access /bin/usr: No such file or directory
echo $?
2
```
Man page often include a section entitled "Exit status," describing what codes are used. a zero always indicates success.

The shell provides two extremely simple builtin commands that do nothing except terminate with either a zero or one exit status. The **true** command always executes successfully and the **false** command always executes unsuccessfully
We can use these commands to see how the **if** statement works. What the **if** 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTEwMDkzNSw4NDUzMzg5MjhdfQ==
-->