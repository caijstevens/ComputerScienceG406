 #nas 

# Memory 

Virtual address space of $V=2^n$ (32/64 bit)
- linux (32-bit) process memory layout
- stack grows towards lower memory addresses
- text and data segments loaded from executable
![[Screenshot 2025-10-13 at 12.28.10.png]]

### Stack and Stack Frame

A **stack** is an abstract data type
- LIFO 
- relevant operations: push and pop
- pointer points to last address on stack (lowest)

Data written to local variables grows towards higher addresses
- **stack frame** is portion of stack allocated to single procedure call
- frame contains function args, local variables and info to restore caller's state
- **frame pointer** and **stack pointer** delimit stack frame
- most info accessed relative to frame pointer, stack pointer can move during execution

# Buffer Overflow 

Two main underlying causes:
- **user data and control info share stack**
- **untrusted input copied into buffer without any bounds checking**
	- affects fixed size buffers
	- languages e.g Java and C# check for these conditions at runtime
	- common error in C caused by unsafe function use e.g. `strcpy(), gets() or sprintf()`
	- incorrect use of safe functions can also lead to buffer overflow![[Screenshot 2025-10-13 at 12.32.17.png]]

### NOP Slide

Assume vulnerable buffer has enough space
- use knowledge of stack frame to guess approximate return address
- insert array of NOPs (\x90) before the shell code.

### Summary 

Objectives of buffer overflow:
- manipulate program control flow
- modify state of program 
- crash program 
- execute arbitrary code

A buffer overflow is mostly interesting if program owner different to executer owner.
- `setuid` is UNIX mechanism that sets user ID upon execution, allows program to be executed with root privileges = very dangerous + powerful

