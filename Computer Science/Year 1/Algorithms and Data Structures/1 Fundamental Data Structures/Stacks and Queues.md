#ads 

### Stacks
A **stack** is a collection of objects that are inserted and removed by **LIFO**
- objects inserted at any time, but only most recently inserted object can be removed at any time

Supports following methods:
- `push(e)`: Insert element e at the top of the stack
- `pop`: Remove and return top element of stack (error if stack empty)
- `size`: Return number of elements in the stack
- `isEmpty`: Return Boolean indicating if stack empty
- `top`: Return top element in stack without removing it (error if stack empty)

In an array based implementation, the stack consists of N-element array S, and integer variable t with top element of stack.
- initialise t to -1, use this value to identify empty stack.

Array based implementation is time efficient.
- does not depend on size of stack
- fixed size N of array can be serious limitation:
	- if size of stack << N, we waste memory
	- if size of stack > N, implementation will generate overflow exception

### Queues
A **queue** is a collection of objects that are inserted and removed by **FIFO**
- element access/deletion restricted to **front** element
- insertion restricted to **rear** of the queue

Supports following methods:
- `enqueue(e)`: Insert element e at the rear of queue
- `dequeue`: Remove and return from queue element at front, error occurs if queue is empty.
- `size`: Return number of elements in queue
- `isEmpty`: Return Boolean indicating if queue is empty
- `front`: Return front element of queue without removing, error occurs if queue is empty.

Array implementation of queue:
- Use two variables f and r:
	- f is index to cell of Q storing front of queue (if queue empty, $f = r$)
	- r is index to next available array cell in Q, the cell after rear of Q if Q is not empty
- Initially we assign $f = r = 0$, indicating queue is empty
- After each enqueue operation we increment r, after each dequeue operation we increment f
- r is incremented after each enqueue operation and never decremented. After N enqueue operations we would get an array-out-of-bounds error.
- To avoid this, let r and f wrap around end of Q, by using module N arithmetic on them.

- If size of queue is N, then $f = r$ and the isEmpty method returns True even though queue is not empty
- We avoid this problem by keeping maximum of elements that can be stored in queue to N-1.
- Array implemented queue is time efficient, all methods run in constant time.
- Capacity of array queue is fixed.


| Operation on LL | Where | Speed* | Stack     | Queue       |
| --------------- | ----- | ------ | --------- | ----------- |
| Insertion at    | Head  | Quick  | Stack.top |             |
| Removal from    | Head  | Quick  |           | Queue.front |
| Insertion at    | Tail  | Quick  |           | Queue.rear  |
| Removal from    | Tail  | Slow   |           |             |
- by **speed**: does no. of operations grow with list size (slow) or stay roughly same (quick)