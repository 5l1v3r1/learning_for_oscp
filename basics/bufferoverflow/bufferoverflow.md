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

We can call the **secretFunction** by just modifying the input. There are better ways to do this if the binary is local. We can use **gdb** to modify the %eip. But in case the binary is running as a service on some other machine, we can make it call other functions or even custom code by just modifying the input.

## Memory Layout of a C program
Let's start by first examining the memory layout of a C program, especially the stack, it's content and it's working during function calls and returns. We will also go into the machine registers **esp**, **ebp**, etc.

## Divisions of memory for a running process
![layout](https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/memory_layout.png)
Source: [https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/memory_layout.png](https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/memory_layout.png)

1. Command line arguments and environment variables:
	The arguments passed to a program before running and the environment variables are stored in this section
2. Stack:
	This is the place where all the function parameters, return addressed and the local variables of the function are stored. It's a **LIFO** structure. It grows downward in memory as new function calls are made. We will examine the stack in more detail later.
3. Heap:
	All the dynamically allocated memory resides here. Whenever we use **malloc** to get memory dynamically, it is allocated from the heap. The heap grows upwards in memory as more and more memory is required.
4. Uninitialized data(Bss Segment): 
	All the uninitialized data is stored here. This consists of all global and static variables which are not initialized by the programmer. The kernel initializes them to arithmetic 0 by default.
5. Initialized data(Data Segment):
	All the initialized data is stored here. This consists of all global and static variables which are initialized by the programmer.
6. Text:
7. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNjY4MjI0MjYsLTM1MDQyNjkzMF19
-->