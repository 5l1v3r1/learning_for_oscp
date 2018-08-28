# Editing The scripts you already have
You already have some scripts of your own. These scripts were put into your home directory when your account was created, and are used to configure the behavior of your session on the computer. You can edit these scripts to change things.

a number of facts about the world in its memory that the system is holding is called the environment. The environment contains such things as your path, your username, the name of the file where your mail is delivered, and much more. You can see a complete list of what is in your environment with the **set** command.

## How is the Environment Established?

When you log on to the system, the bash program starts, and reads a series of configuration scripts called **startup files**. These define the default environment shared by all user. These sequence depends on the type of shell session being started. There are two kinds:
- a login shell session
- a non-login shell session
Login shells read one or more startup files as shown below:

|File|Contents|
|:--|:--|
|/etc/profile|A global configuration script that applies to all users.|
|~/.bash_profile|A user's personal startup file. Can be used to extend or override settings in the global configuration script.|
|~/.bash_login|If ~/.bash_profile is not found, bash attempts to read this script.|
|~/.profile|If neither ~/.bash_profile nor ~/.bash_login is found, bash attempts to read this file.|

Non-login shell sessions read the following startup files:

|File|Contents|
|:---|:--|
|/etc/bash.bashrc|A global configuration script that applies to all users.|
|~/.bashrc|A user's personal startup file. Can be used to extend or override settings in the global configuration script.|

Non-login shells inherit the environment from their parent process, usually a login shell.

**.bash_profile** looks something like this:
```bash
# .bash_profile
# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs
PATH=$PATH:$HOME/bin
export PATH
``` 

## Aliases
An alias is an easy way to create a new command which acts as an abbreviation for a longer one. I has the following syntax:
```bash
alias name=value
```
Let create an alias called "l" and make it an abbreviation for the command "ls-l".
Using your favorite text editor, open the file .bashrc and add this line to the end of the file:
```bash
alias l='ls -l'
```
Here is another one for you to try:
```bash
alias today='date +"%A, %B -%-d, %Y"'
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyOTgxMzgyMDddfQ==
-->