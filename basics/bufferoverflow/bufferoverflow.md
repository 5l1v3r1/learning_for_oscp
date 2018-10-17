# Buffer Overflow Exploit
quoted from [this site](https://dhavalkapil.com/blogs/Buffer-Overflow-Exploit/)

## Introduction
We will simply exploit the buffer by smashing the stack and modifying the return address of the function. This will be used to call some other function. You can also use the same technique to point the return address to some custom code that you have written, thereby executing anything you want.

## Prerequisites
1. have basic-intermediate knowledge of **C**.
2. be a little familiar with **gcc** and the linux command line.
3. Basic x86 assembly language.

## Machine Requirements
latest distro's of **linux**. We are going to create a 32 bit binary.

## Sample Vulnerable program
```c
#include <stdio.h>

void secretFunction()
{
	printf("Congratulations!\n");
	printf("You have entered in the secret function!\n");
}

void echo() 
{
	char buffer[20];
	
	printf("Enter some text:\n");
	scanf("%s", buffer);
	printf("You entered: %s\n", buffer);
}

int main()
{
	echo();
	return 0;
}
```

We can call the **secretFunction** by just modifying the input. There are better ways to do this if the binary is local. We can use **gdb** to modify the %eip. But in case the binary is running as a service on some other machine, we can make it call other functions or even custom code by 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIwMTE1OTE5NiwtMzUwNDI2OTMwXX0=
-->