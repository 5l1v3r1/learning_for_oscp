# Errors and signals and traps - part1
In this lesson, we're going to look at handling errors during the execution of your scripts.
The difference between a good program and a poor one is often measured in terms of the program's robustness. That is, the program's ability to handle situations in which something goes wrong.

## Exit status
It is very important to check the exit status of programs you call in your scripts. It is also important that your scripts return a meaningful exit status when they finish.

## Checking the exit status
You can examine the contents of the $? environment variable to 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTkwNzg4OCwtMjA4ODc0NjYxMl19
-->