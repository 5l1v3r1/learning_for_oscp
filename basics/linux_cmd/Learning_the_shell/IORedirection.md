# I/O Redirection
we can redirect the output of many commands to files, devices, and even to the input of other commands.

## Standard Output
Standard output directs its contents to the display. To redirect standard output to a file, the ">" character is used like this:
```bash
[me@linuxbox me]$ ls > file_list.txt
```
If you want the new results to be appended to the file instead, use ">>" like this:
```bash
[me@linuxbox me]$ ls >> file_list.txt
```

## Standard Input
Many commands can accept input from a facility called standard input. By defau
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxNjcxMjEzOF19
-->