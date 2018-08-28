# Writing your first script and getting it to work
To successfully write a shell script, you have to do three things:
1. Write a script
2. Give the shell permission to execute it
3. Put it somewhere the shell can find it

## writing shell script
Now, fire up your text editor and type in your first script as follows:
```bash
#!/bin/bash
#My first script
echo "Hello world!"
```
The first line of the script is called a shebang, given to the shell indicating what program is used to interpret the script.
The second line is a comment.t

## Setting Permission
We have to give the shell permission to execute your script.
```bash
[me@linuxbox me]$ chmod 755 hello_world
```

## Putting it in your path
Try this:
```bash
[me@linuxbox me]$ ./hello_world
```
You should see "Hello World!" displayed.

the shell maintains a list of directories where executable files are kept, and only search the directory in that list.
This list of directories is called your path. You can view the list 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2NzY5MDg1NCw4ODgwMTM3XX0=
-->