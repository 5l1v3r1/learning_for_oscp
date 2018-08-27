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
the tilde character ("~") has a special meaning. When used at the beginning of a word., it expands into the name of the home directory of the named use


<!--stackedit_data:
eyJoaXN0b3J5IjpbNTIxNDc4NjkwXX0=
-->