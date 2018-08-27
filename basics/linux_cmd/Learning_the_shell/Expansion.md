# Expansion
The process before shell carries out your command is called **expansion**. With expansion, you type something and it is expanded into something else before the shell acts upon it. 
Example of Expansion:
```bash
[me@linuxbox me]$ echo *
```

## Pathname Expansion
The mechanism by which wildcards work is called **pathname expansion**. 
we can carry out following expansion:
```bash
ls
```
```bash
echo D*
```
```bash
echo *s
```
```bash
echo [[:upper:]]*
```

## Tilde Expansion
the tilde character ("~") has a special meaning. When used at the beginning of a word., it expands into the name of the home directory of the named user.
```bash
echo ~
/home/me
```
```bash
echo ~foo
/home/foo
```

## Arithmetic Expansion
The shell allows arithmetic to be performed by expansion. This allows us to use the shell prompt as a calculator:
```bash
[me@linuxbox me]$ e


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI5MTE4ODU3NF19
-->