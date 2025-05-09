#ads 

### Arrays
A sequence of **elements** $a_1, a_2, ..., a_n$ is called an **array** and usually denoted by something like $A[1], A[2], ..., A[n]$ or $A[1 ... n]$ 
- in consecutive memory cells
- all elements of same **type**

Arrays are **contiguous** and **homogeneous** which has its pros and cons...

### Linked Lists
A **list** is made up of **nodes**. Each stores an element plus a **link** to another node.
- the first node is called the **head**
- the last node (**tail**) points to null
- nodes may be scattered around memory

|                         | Array | Linked List |
| ----------------------- | ----- | ----------- |
| **Data Access**         | fast  | slow        |
| **Insertion, Deletion** | slow  | fast        |

### Doubly Linked Lists
A node in a **doubly linked list** stores two references:
- a next link
- a prev link

to simplify, add two **dummy** nodes at end of doubly linked list:
- header has valid next ref but null prev ref
- trailer has valid prev ref but null next ref

DLL also needs to store refs to two sentinel nodes and size counter keeping track of number of nodes in list (excluding sentinels).

An empty list would have two sentinel nodes pointing to each other.

### Circularly Linked Lists
Has same kind of nodes as singly linked list. Each node has next pointer and element ref.

Circularly linked list has no beginning or end. Last node's next pointer is to first node.

No head/tail: mark node of CLL as cursor, which is starting node upon traversing list.