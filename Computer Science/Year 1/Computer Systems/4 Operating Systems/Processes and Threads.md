#cs 

### Processes 

> [!info] Definition 
> A **process** is a program in execution
> 

OS executes variety of programs
- batch system - jobs
- time-shared systems - user programs/tasks

OS is responsible for process management
- creation/deletion
- holding and resuming
- mechanisms for process synchronisation (priority, scheduling)

**Process Concept**:
- code: text section 
- current activity, represented by PC and content of CPU registers
- stack: temp data, local variables
- data section: global variables
- heap: memory allocated while process running![[Screenshot 2025-05-19 at 14.30.59.png]]
**Process Control Block**:
- contains info about each process
- unique identifier
- state (~ status)
- CPU registers
- CPU scheduling (priority)
- memory usage
- accounting, I/O status etc

### Process State 

As process executes, changes state (~ status):
- **New** - process being created
- Running - instructions being executed
- Waiting - process waiting for some event
- Ready - process ready for dispatch to CPU
- **Terminated** - process execution complete or other event causing termination![[Screenshot 2025-05-19 at 14.33.55.png]]
### Process Creation and Termination

**Creation**: New process can create several child processes - forms tree
- Resource sharing: 3 possible cases
	1. parent and child processes share all resources
	2. child shares subset of parent resources
	3. parent and child share no resources
- Execution: 2 possible cases
	1. parent and child execute concurrently
	2. parent waits until child terminates

Creation and address space:
- child duplicates parent address space
- easier parental communication 
- e.g. UNIX, `fork()` creates new process, and `exec()` used afterwards to replace process memory space with new program
![[Screenshot 2025-05-19 at 14.37.24.png]]

**Termination**: process executes last statement and asks OS to delete using `exit()` syscall:
- outputs data from child to parent
- child's resources de-allocated by OS

Parent may terminate execution of child if:
- child exceeds allocated resources
- task assigned to child no longer required
- parent terminating itself (cascade)


| Status Change                    | Process Description                        |
| -------------------------------- | ------------------------------------------ |
| Running $\rightarrow$ Terminated | Process exits                              |
| Ready $\rightarrow$ Running      | Process selected to run on processing core |
| Running $\rightarrow$ Ready      | Timeout has occurred                       |
| Running $\rightarrow$ Waiting    | Process needs to wait for an event         |
| Waiting $\rightarrow$ Ready      | Event being waited on has occurred         |


### Process Scheduling 

Maximises CPU use by quickly switching processes onto CPU for time sharing
- **process scheduler** selects processes for next execution 
- maintains scheduling queues of processes
	- **job queue**: set of all processes in system
	- **ready queue**: set of all processes in main memory waiting to execute 
	- **device queues**: set of processes waiting for I/O device ![[Screenshot 2025-05-19 at 15.33.52.png]]

### The Kernel 

Aim: to provide environment in which processes can exist

Components:
- privileged instruction set
- interrupt mechanism
- memory protection
- real-time clock

Consists of:
- **first-level interrupt handler** (FLIH)
	- determines interrupt source
	- initiate servicing
- **dispatcher** (scheduler)
	- assigns processing resource for processes 
	- initiated when current process cannot continue, decides if CPU better used elsewhere
- intra operating system communications 

### Threading 

**Threads** are a unit of execution
- can be traced, list sequence of instructions that execute
- belongs to a process and executes within it
- can be a user thread or kernel thread 

**Multithreading**: OS supports multiple threads within a single process

**Single threading**: OS does not recognise separate concept of thread 
![[Screenshot 2025-05-19 at 15.42.50.png]]
![[Screenshot 2025-05-19 at 15.43.06.png]]

**Thread Model**:
- local variables per thread allocated on stack (each thread has own stack)
- global variables shared between all threads: allocated in data section, concurrency control can be issue
- dynamically allocated memory can be local or global (program defined)

**Threading Benefits**:
- **Timing**: quicker to create/terminate/switch thread than process
- **Responsiveness**: can allow continued execution if part of process is blocked
- **Resource Sharing**: threads share process resources (easier than shared memory etc)
- **Economy**: cheaper than process creation
- **Scalability**: process can use multiprocessor architectures

![[Screenshot 2025-05-19 at 15.46.27.png]]

### Amdahl's Law

Identifies performance gains by adding additional cores to app that has serial and parallel components.

$$speedup \leq\frac{1}{S+\frac{(1-S)}{N}}$$
- $S$ is serial portion, $N$ cores
- e.g. if application 75% parallel 25% serial, moving from 1 to 2 cores means speedup of 1.6x
- As $N\rightarrow\infty,\space speedup\rightarrow \frac{1}{S}$

### Multithreading Models 

1. **Many-to-One**
	- many user-level threads map to single kernel thread 
	- one thread block = all block
	- no parallel on multicore because only one in kernel at a time
![[Screenshot 2025-05-19 at 15.54.10.png]]
2. **One-to-One**
	- each user thread maps to one kernel thread 
	- create user thread creates kernel thread 
	- more concurrency than M-to-O
	- threads per process restricted by overhead
![[Screenshot 2025-05-19 at 15.54.23.png]]
3. **Many-to-Many**
	- many user level threads to many kernel level threads
	- allows OS to create sufficient number of kernel threads
![[Screenshot 2025-05-19 at 15.55.28.png]]

**Thread library** provides API for creating/managing threads. Can implement by either:
- library entirely in user space
- kernel-level library supported by OS