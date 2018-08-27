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
[me@linuxbox me]$ echo $((2 + 2))
4
```
```bash
[me@linuxbox me]$ echo $(($((5**2)) * 3))
75
```

## Brace Expansion
With brace expansion, you can crate multiple text strings from a pattern containing braces. Here's an example:
```bash
echo Front-{A,B,C}-Back
```
Here is an example using a range of integers:
```bash
echo Number_{1..5}
```
A range of letters in reverse order:
```bash
echo {Z..A}
```
Brace expansion may be nested:
echo a{A{1,2},B{3,4}}b

This expansion is used to make lists of files or directories to be created like this:
```bash
mkdir {2007..2009}-0{1..9} {2007..2009}-{10..12}
```

## Parameter Expansion
it can expands variables. For example, the variable named "USER" contains your username. To invoke parameter expansion and reveal the contents of USER you would do this:
```bash
echo $USER
```
To see 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzAzNDgzMDBdfQ==
-->