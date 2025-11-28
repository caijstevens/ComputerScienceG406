#cs 

### Multiprogramming

**Maximises** CPU utilisation
- several processes kept in memory concurrently
- one process **waiting**, OS executes one of the processes sitting in the **ready** queue

CPU Scheduling used to support multiprogramming in process management.

### CPU Scheduling 

Processes "take turns"
- sharing of system resources
- scheduling fundamental to OS design

OS operates 3 types of **scheduler**:
- **Long-term scheduler (job scheduler)** selects which processes brought into ready queue
- **Medium-term scheduler** part of swapping, handles swapped out processes
- **Short-term scheduler (CPU scheduler)** selects process to be executed next and allocated to CPU


> [!info] Definition
> **Dispatcher**: Module that gives control of CPU to the Process chosen by scheduler

Functions involved:
- **Switching context**: context-switch time is an overhead, the system undertakes no user processing while switching
- Switching to User Mode 
- Jumping to proper location in user program to restart program

**Dispatch Latency**: time it takes for dispatcher to stop one process and start another running.

> [!success] Scheduling Criteria
> 1. **CPU utilisation**: keep CPU busy
> 2. **Throughput**: number of processes that complete execution per unit time
> 3. **Turnaround time**: amount of time to execute particular process
> 4. **Waiting time**: total amount of time process has been waiting in ready queue
> 5. **Response time**: amount of time between request submission until first response (access to CPU)

> [!success] Optimisation Criteria
> 1. Max CPU utilisation
> 2. Max throughput
> 3. Min Turnaround time
> 4. Min Waiting time
> 5. Min Response time

### Scheduling Algorithms 

> [!example] Different Scheduling Algorithms
> 1. First Come, First Served (FCFS)
> 2. Shortest Job First (SJF)
> 3. Shortest Remaining Time First (SRTF)
> 4. Priority (with or without pre-empting)
> 5. Priority (with or without ageing)
> 6. Round-Robin (RR)
> 7. Multilevel queue/feedback queue

### First Come, First Served (FCFS)

**Basic Definition**: The first process to request the CPU is allocated the CPU until it is completed.
- average wait time may be lengthy
- simple algorithm
- short processes can have to wait for long ones to finish
![[Screenshot 2025-05-19 at 19.27.55.png]]

### Shortest Job First (SJF)

**Basic Definition**: As processes arrive, the shorter the CPU burst requirement, the further forward in the ready queue the process is placed.

Associate with each process the length of its next CPU burst
- use lengths to schedule process with shortest time (FCFS if two have same time)
- non pre-emptive: once CPU given to process, cannot be pre-empted until process has completed CPU burst
![[Screenshot 2025-05-19 at 19.40.46.png]]

SJF is optimal - minimum average waiting time for given set of processes.
- difficulty is knowing length of next CPU request

### Shortest Remaining Time First (SRTF)

**Basic Definition**: Pre-emptive version of SJF. If a new process is shorter than remaining time of current process' CPU burst, then new process gets priority.
- pre-empt running process and run process with shorter CPU burst length.
![[Screenshot 2025-05-19 at 19.50.55.png]]

### Round Robin (RR)

**Basic Definition**: Each process gets small unit of CPU time and is added to end of ready queue at end of time slice.
- usually time slice $10 \leq q \leq 100$ milliseconds
- if $n$ processes in ready queue and time quantum is $q$, each process gets $1/n$ of CPU time in chunks of at most $q$ time units at once.
![[Screenshot 2025-05-19 at 19.55.36.png]]

Performance depends on q size.
- if $q$ is large, RR policy same as FCFS
- if $q$ is very small (1ms), RR can result in large number of context switches
- turnaround time depends on $q$
- rule of thumb: $80\%$ of CPU bursts should be shorter than $q$

### Priority Scheduling

In **Priority Scheduling**, algorithm associates priority number for each process.
- CPU allocated by dispatcher to process with highest priority (smallest integer = highest priority)
- can be pre-emptive or not
![[Screenshot 2025-05-19 at 20.16.06.png]]

Problem: **Starvation** (indefinite blocking), low priority processes may never execute
- Solution: **Ageing**, as time progresses increase process priority
- or, combine RR with priority

### MultiLevel Queue 

**Ready** queue partitioned into separate queues with own scheduling algorithm
- allows for foreground and background queues
- scheduling must be undertaken between queues, fixed priority or timeslice scheduling.![[Screenshot 2025-05-19 at 20.21.33.png]]
- Problem: provides differentiation but not flexible; process remains in same queue even if requirements adapted.

### MultiLevel Feedback Queue 

**Feedback queues** are an adaption of multilevel queue scheduling
- process can move between queues, ageing can be implemented
- scheduler defined by following parameters:
	- number of queues
	- scheduling algorithms for each queue
	- method for determining when to upgrade/demote process
	- method used to determine queue process will enter


> [!info] Little's Formula
> $n=\lambda \times W$ where $n$ is avg. long-term queue length, $W$ is avg. waiting time in queue, $\lambda$ is avg. arrival rate for new processes in queue


