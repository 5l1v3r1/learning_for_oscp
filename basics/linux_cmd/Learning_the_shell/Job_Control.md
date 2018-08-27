# Job Control
There are several commands that can be used to control processes. They are:
- **ps** - list the processes running on the system
- **kill** - send a signal to one or more process
- **jobs** - an alternate way of listing your own processes
- **bg** - put a process in the background
- **fg** - put a process in the forground

## Putting a program in the background
Now, we are going to launch the **xload** program in the background so that prompt will return.
```bash
[me@linuxbox me]$ xload &
```
you can do the same thing using the **bg** command.
```bash
[me@linuxbox me]$ xload
[me@linuxbox me]$ bg
```

## Listing your process
To display a list of the processes we have launched, we can use either the **jobs** command or the more powerful **ps** command.
```bash
[me@linuxbox me]$ jobs
```
```bash
[me@linuxbox me]$ ps
```

## Killing a process
When you wish to get rid of a program that become unresponsive, you can use the **kill** command. First, you need to identify the process you want to kill. You can use either **jobs** or **ps**, to do this. If ou use **jobs** you will get back a job number. With **ps**, you are given a process id
```bash
xload &
jobs
kill %1
xload &
ps
kill 1293
```

## A little more about kill
kill command can send a variety of signals to process. Typing `kill -l` will give you a list of the signals it supports.

|Signal|Name|Description|
|:--|:--|:--|
|1|SIGHUP|Hang up signal. Programs can listen for this signal and act upon it. This signal is sent to processed running in a terminal when you close the terminal.|
|2||SIG



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzM1NTUzODUsLTI3MDc0ODMzMV19
-->