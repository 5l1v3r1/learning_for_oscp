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
We can use these commands to see how the **if** statement works. What the **if** statement really does is evaluate the success or failure of commands:
```bash
if true; then echo "It's true."; fi
It's true.
if false; then echo "It's true."; fi

```

## test
The **test** command is used most often with the **if** command to perform true/false decisions. The command is unusual in that it has two different syntactic forms.
```bash
# first form
test *expression*
# second form
[ expression ]
```
The test command works simply. If the given expression is true, test exits with a status of zero; otherwise it exits with a status of 1. The neat feature of test is the variety of expressions you can create.
```bash
if [ -f .bash_profile ]; then
	echo "You have a .bash_profile. Things are fine."
else
	echo "Yikes! You have no .bash_profile!"
fi
```

Here is a partial list of the conditions that test can evaluate.
|Expression|Description|
|:--|:--|
|-d file|True if file is a directory|
|-e file|True if file exists.|
|-f file|True if file exists and is a regular file.|
|-L file|True if file is a symbolic link.|
|-r file|True if file is a file readable by you|
|-w file|True if file is a file writable by you|
|-x file|True if file is a file executable by you|
|file1 -nt file2|True if file1 is newer than file2|
|file1 -ot file2|True if file1 is older than file2|
|-z string|True if string is empty|
|-n string|True if string is not empty|
|string1 = string2|True if string1 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3ODQxMzUyNSw4NDUzMzg5MjhdfQ==
-->