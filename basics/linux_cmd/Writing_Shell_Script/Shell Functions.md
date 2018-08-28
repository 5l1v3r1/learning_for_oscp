# Shell Functions
As programs get longer and more complex, they become more difficult to design, code, and maintain. As with any large endeavor, it is often useful to break a single, large task into a series of smaller tasks.
The process of identifying the top-level steps and developing increasingly detailed views of those steps is called top-down design. This technique allows you to break large complex tasks into many small, simple tasks.
If we look at our script's top-level tasks, we find the following list:

1. Open page
2. Open head section
3. Write title
4. Close head section
5. Open body section
6. Write title
7. Write time stamp
8. Write system release info
9. Write up-time
10. Write drive space
11. Write home space
12. Close body section
13. Close page

 If there were commands that performed these tasks, we could use command substitution to place them in our script like so:
```bash
#!/bin/bash

# sysinfo_page - A script to produce a system information HTML file

##### Constants

TITLE="System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

##### Main

cat <<- _EOF_
  <html>
  <head>
      <title>$TITLE</title>
  </head>

  <body>
      <h1>$TITLE</h1>
      <p>$TIME_STAMP</p>
      $(system_info)
      $(show_uptime)
      $(drive_space)
      $(home_space)
  </body>
  </html>
_EOF_
```
While there are no commands that do exactly what we need, we can create them using shell functions. To ad the shell functions to our script, we change it so:
```bash
#!/bin/bash

# sysinfo_page - A script to produce an system information HTML file

##### Constants

TITLE="System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

##### Functions

system_info()
{

}


show_uptime()
{

}


drive_space()
{

}


home_space()
{

}

##### Main

cat <<- _EOF_
  <html>
  <head>
      <title>$TITLE</title>
  </head>

  <body>
      <h1>$TITLE</h1>
      <p>$TIME_STAMP</p>
      $(system_info)
      $(show_uptime)
      $(drive_space)
      $(home_space)
  </body>
  </html>
_EOF_
```

A couple of important points about functions: First, they must appear before you attempt to use them. Second, the function body must contain at least one valid command. After you place a **return** statement in each function body, our script will execute successfully.

## Keep Your Script Working
When you are developing a program, it is often a good practice to add a small amount of code, run the script, add some more code, run the script, and so on.

As you add functions to your script, you can use a technique called **stubbing**.
Is is
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDE3Nzk5NzBdfQ==
-->