# Working With Commands
This lesson will introduce you the following commands.
- **type** - Display information about command type
- **which** - Locate a commands
- **help** - Display reference page for shell builtin
- **man** - Display an on-line commands reference

## What are "Commands"?
Commands can be one of 4 different kinds:
1. An executable program
2. A command built into the shell itself
3. A shell function
4. An alias

## Identifying Commands
### type
The **type** commands is a shell builtin that display the kind of commands the shell will execute, given a particular command name.
```bash
type command
```
```bash
[me@linuxbox me]$ type type
type is a shell builtin

[me@linuxbox me]$ type ls
ls is aliased to 'ls --color=tty'

[me@linuxbox me]$ type cp
cp is /bin/cp
```

### which
The **which** command is used to determine the exact location of a 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwOTcyMjU1NDhdfQ==
-->