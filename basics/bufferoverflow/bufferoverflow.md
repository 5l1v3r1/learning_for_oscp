# Buffer Overflow Exploit
quoted from [this site](https://dhavalkapil.com/blogs/Buffer-Overflow-Exploit/)

## Introduction
We will simply exploit the buffer by smashing the stack and modifying the return address of the function. This will be used to call some other function. You can also use the same technique to point the return address to some custom code that you have written, thereby executing anything you want.

## Prerequisites
1. have basic-intermediate knowledge of **C**.
2. be a little familiar with **gcc** and the linux command line.
3. Basic x86 assembly language.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTcxMjcxMTEsLTM1MDQyNjkzMF19
-->