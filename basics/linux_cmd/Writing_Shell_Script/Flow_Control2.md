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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExOTQ5MTMzMDJdfQ==
-->