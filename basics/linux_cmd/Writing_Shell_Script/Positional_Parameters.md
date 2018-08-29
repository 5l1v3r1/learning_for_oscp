# Positional Parameters
there are several more features I want to add our script:

1. I want to specify the name of the output file on the command line, as well as set a default output file name if no name is specified.
2. I want to offer an interface mode that will prompt for a file name and warn the user if the file exists and prompt the user to overwrite it.
3. Naturally, we want to have a help option that will display a usage message.

To handle options on the command line, we use a facility in the shell called **positional parameters**. Positional parameters are series of special variables that contain the contents of the command line. 
Let's imagine the following command line:
```bash
[me@linuxbox me]$ some_program word1 word2 word3
```
we could reach each item on the command line because the positional parameters contains the followingl:
- $0 would contain "some_program"
- $1 would con
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTE1Mzk3NTUxXX0=
-->