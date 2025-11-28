 #cs 

### Operating Systems 

Why operating system needed
1. OS is abstract machine
	- extends hardware, adds functionality
	- high-level abstraction: programmer friendly, common core for all applications
	- hides hardware details - code more portable
2. OS is resource manager
	- responsible for allocating resources to users and processes
	- must ensure:
		- no starvation
		- progress
		- allocation by policy (FIFO etc)
		- efficient use


> [!info] Definition
> An **operating system** is a program that acts as an intermediary between a user and the hardware.

Goals:
- execute programs
- simplify problem solving 
- increase convenience
- fair and efficient resource use

### Computer System Structure 

**Hardware**: basic computing resources
 - CPU, memory, I/O etc

**Operating System**:
- controls hardware use among various apps/users

**Application Programs**: define how system resources used for solving user problems
- e.g. word processors, compilers, games, browsers etc

**Users**:
- people, machines, other computers etc
![[Screenshot 2025-05-19 at 13.37.01.png]]


OS is:
- **resource allocator**: manages computer system resources
- **control program**: controls program execution and I/O device operation to prevent errors and improper computer use
- **kernel**: the one program that is always running

### OS Operations

OS kernel runs in **privileged mode**:
- contains functionality required to implement other services and provide security
- apps should not interfere with or bypass OS
- OS can enforce resource allocation policies and prevent app interference

**Dual-mode** operation allows OS to protect self and other components
- **user mode** and **kernel mode** (see above)
- has **mode bit** provided by hardware, distinguishes whether OS is running user or kernel code
- some instructions are **privileged**, only executable in kernel mode
- system call = mode change to kernel, return from call = reset to user

Privileged instructions include:
- managing interrupts
- I/O operations
- halting processes

Switches from user to kernel mode when:
- user process calls on OS to execute, requiring privileged instruction (sys call)
- interrupt occurs
- error condition in user process
- attempt to execute privileged instruction in user mode
![[Screenshot 2025-05-19 at 13.44.24.png]]

Other OS management operations:
- resources
- processes
- memory
- mass storage
- file system
- cache
- I/O system 


### Operating System Types 

**Multi-user**:
- 2+ users can run programs simultaneously

**Multi-programming**:
- supports running program on more than 1 CPU

**Multi-tasking**:
- more than one program running concurrently

**Multi-threading**:
- allows different parts of single program to run concurrently

**Real Time**:
- responds to input instantly



**Multiprogramming** needed for efficiency
- single user cannot keep CPU and I/O busy at all times
- MP organises code/data so CPU always executing
- total jobs subset stored in memory
- job selected and run (job scheduling)
- when waiting, OS switches to another job

**Timesharing (multitasking)** is where CPU constantly switches jobs so users can interact with jobs while running - **interactive computing**
- each user has at least one executing program
- **CPU scheduling** if several jobs ready to run same time
- if processes don't fit, **swapping** moves them in and out to run
- **virtual memory** allows process execution not completely in memory

### Operating System Services

![[Screenshot 2025-05-19 at 13.53.36.png]]

One set of OS services provides functions helpful to user
- **User Interface**: almost all OS have UI, can be **Command Line (CLI), Graphical User Interface (GUI), Batch**
- **Program execution**: system must be able to load and run program and end execution (normally/abnormally with error)
- **I/O operations**: program may require I/O which may involve file or I/O device 
- **File system manipulation**: programs need to read/write files/directories, as well as create/delete, search, list file info and manage permissions
- **Communications**: processes may exchange info, on same or different computers on network, through shared memory or message passing
- **Error detection**: OS constantly aware of possible errors everywhere, take appropriate action and have debugging facilities

Other set of OS functions help efficient system operation via resource sharing
- **Resource allocation**: multiple concurrent users or running jobs, resources allocated to all
- **Accounting**: keep track of usage per user and types of computer resources
- **Protection and security**: ensure that all access to system resources is controlled, and require user authentication to protect from unauthorised/invalid access attempts

### CLI and GUI

**CLI** or **command interpreter** allows direct command entry
- implemented in kernel or by systems program
- sometimes uses multiple flavours - **shells**
- fetches command from user and executes
- commands built-in or names of programs

**GUI** is user friendly desktop interface
- mouse, keyboard, monitor
- **icons** for files, programs etc
- mouse buttons $\rightarrow$ various functions 

### Design and Implementation

**User** goals and **System** goals:
- **User**: OS should be convenient, easy to learn, reliable, safe and fast
- **System**: OS should be easy to design, implement and maintain, flexible, reliable, error-free and efficient

**Policy** (what to do) vs **mechanism** (how to do it)
- separation allows flexibility if policy decisions changed later

### OS Structure 

**Simple Structure - MS-DOS**:
- provide most functionality in least space
- not divided into modules
- interfaces and functionality levels not well separated![[Screenshot 2025-05-19 at 14.16.55.png]]
**Non-Simple Structure - UNIX**:
- single file, single address space (monolithic)
- separated into **systems programs** and the **kernel**
- kernel is everything below syscall interface and above hardware 
![[Screenshot 2025-05-19 at 14.18.32.png]]


**Layered Approach** - unrealistic
- OS divided into layers built on top of each other
- bottom layer hardware, highest is UI
- modularity: layers selected so each uses functions and services of only lower layers

**Microkernel system structure**:
- moves as much from kernel into user psace
- communication between user modules uses message passing
- non-ideal performance transferring from user space to kernel space 
![[Screenshot 2025-05-19 at 14.22.14.png]]

