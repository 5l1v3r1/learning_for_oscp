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
	This is the section where the executable code is stored. The loader loads instruction from here and executes them. It is often read only.

## Some common registers
1. %eip
	The **Instruction Pointer Register**. It stores the address of the next instruction to be executed. After every instruction execution it's value is incremented depending upon the size of an instruction.
2. %esp
	The **Stack Pointer Register**. It stores the address of the top of the stack. This is the address of the last element on the stack. The stack grows downward in memory. So the %esp points to the value in stack at the lowest memory address.
3. %ebp
	The **Base Pointer Register**. The %ebp register usually set to %esp at the start of the function. This is done to keep tab of function parameters and local variables. Local variables are accessed by subtracting offsets from %ebp and function parameters are accessed by adding offsets to it as you shall see in the next section.

## Memory management during function calls
Consider the following piece of code
```c
void func(int a, int b)
{
	int c;
	int d;
	// some code
}
void main()
{
	func(1, 2);
	// next instruction
}
```
Assume our %eip is pointing to the **func** call in **main**. The following steps would be taken.
1. A function call is found, push parameters on the stack from right to left(in reverse order). So 2 will be pushed first and then 1.
2. We need to know where to return after **func** is completed, so push the address of the next instruction on the stack.
3. Find the address of func and set %eip to that value. The control has been transferred to func().
4. As we are in a new function we need to update %ebp. Before updating we save it on the stack so that we can return later back to **main**. So %ebp is pushed on the stack.
5. Set %ebp to be equal to %esp. %ebp now points to current stack pointer.
6. Push local variables onto the stack/reserver space for them on stack. %esp will be changed in this step.
7. After **func** gets over we need to reset the previous stack frame. So set %esp back to %ebp. Then pop the earlier %ebp from stack, store it back in %ebp. So the base pointer register points back to where it pointed in main.
8. Pop the return address from stack and set %eip to it. The control flow comes back to main, just after the **func** function call.

This is how the stack would look while in **func**
![](https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/stack.png)
Souce: [https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/stack.png](https://dhavalkapil.com/assets/images/Buffer-Overflow-Exploit/stack.png)

## Buffer overflow vulnerability
Buffer overflow is a vulnerability in low level codes of C and C++. An attacker can cause the program to crash, make data corrupt, steal some private information or run his/her own code.
It basically means to access any buffer outside of it's allocated memory space. This happens quite frequently in the case of arrays. Now as the variables are stored together in stack/heap/etc. accessing any out of bound index can cause read/write of bytes of some other variable. Normally the program
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyMzQ4ODIzMCwtMTMxNTYyNzA3OSwtMz
UwNDI2OTMwXX0=
-->