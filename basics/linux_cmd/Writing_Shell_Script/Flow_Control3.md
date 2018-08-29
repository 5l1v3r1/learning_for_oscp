# Flow Control - Part 3
Now, it is time to cover the remaining flow control statement, **for**. for works like this:
```bash
for variable in words; do
	commands
done
```
```bash
#!/bin/bash

for i in word1 word2 word3; do
	echo $i
done
```
we can construct the list of words using command substitution, all kinds of expansions.
```bash
#!/bin/bash

count=0
for i in $(cat ~/.bash_profile); do
	count=$((count + 1))
	echo "Word $count ($i) contains $(echo 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4OTM5NDIwNl19
-->