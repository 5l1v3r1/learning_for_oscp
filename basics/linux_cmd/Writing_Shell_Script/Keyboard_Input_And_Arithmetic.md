# Keyboard Input And Arithmetic
In this lesson, we will see how your scripts can ask question, and get and use response.

## read
To get input from the keyboard, you use the **read** command. It takes input from the keyboard and assigns it to a variable.
```bash
echo -n "Enter some text-> "
read text
echo "You entered: $text"
```
If you don't give it the name of a variable to assign its input, it will use the environment variable *REPLY*.

The read command also takes some options. The -t option followed b
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgzMjA5MzIzNF19
-->