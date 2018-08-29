# Flow Control - Part2
## More Branching
There is a second and more complex than the **if** command kind of branching called a **case**. A case is multiple-choice branch.
It could be used like this:
```bash
#!/bin/bash

echo -n "Enter a number between 1 and 3 inclusive > "
read character
case $character in
	1 ) echo "You entered one."
		  ;;
	2 ) echo "You entered two."
		  ;;
	3 ) echo "You entered three."
		  ;;
	* ) echo "You did not enter a number between 1 and 3."
esac
```
Patterns can be literal text or wildcards. Here is a more advanced example.
```bash
#!/bin/bash

echo -n "Type a digit or a letter > "
read character
case $character in
	[[:lower:] | [:upper:]] ) echo "You typed the letter $character"
		;;
	[0-9] ) echo "You typed the digit $character"
		;;
	* ) echo "You did not type a letter or a digit"
esac
```

## Loops
Looping is repeatedly executing a section of your program based on the exit status of a command. The shell provides three commands for looping: **while**, **untill**, **for**.

Here is a simple example of a program that counts from zero to nine:
```bash
#!/bin/bash

number=0
while [ "$number" - lt 10 ]; do
	echo "Number = $number"
	number=$((number + 1))
done
```

The **until** command works exactly the same way, except the block of code is repeated as long as the specified command's exit status is false.
```bash
#!/bin/bash

number=0
until [ "$number" -ge 10 ]; do
	echo "Number = $number"
	number=$((number + 1))
done
```

## Building a Menu
Using the until command and the case command, you can build a simple menu driven application:
```bash
#!/bin/bash

selection=
until [ "$selection" = "0" ]; do
	echo "
	PROGRAM MENU
	1 - Display free disk space
	2 - Display free memory
	0 - exit program
"
	echo -n "Enter selection: "
	read selection
	echo ""
	case $selection in
		1 ) df ;;
		2 ) free ;;
		0 ) exit ;;
		* ) echo "Please enter 1, 2, 0"
	esac
done
```
To make this program better looking when it runs, we can enhance it by adding a function that asks the user to press the Enter key after each selection has bee
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAyNTIwOTg2NF19
-->