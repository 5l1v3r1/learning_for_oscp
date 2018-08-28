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

The read command also takes some options. The -t option followed by a number of seconds provides an automatic timeout for the read command. The -s option caused the user's typing not to be displayed. This is useful when you are asking the user to type in a password or other confidential information.

## Arithmetic
If you want to use the command line as a primitive calculator, You do it like this:
```bash
echo $((2+2))
echo $(( 2+2 ))
echo $(( 2 + 2 ))
```
* whitespace is ignored
* leading "$" is not needed to reference variables inside the arithmetic expression 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyMTQ3MDYzOV19
-->