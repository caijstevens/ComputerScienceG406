#ads 

### Priority Queues

>[!info] DEFINITION:
>A **priority queue** is a data structure in which each element is associated with a priority, and elements are dequeued in order of priority rather than order of insertion. Commonly implemented using heaps to allow efficient retrieval and updating of highest-priority element.

Operations:

| operation      | explanation                                                                                                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| P.add(k, v)    | Insert an item with key k and value v into priority queue P                                                                                                                           |
| P.min()        | Return a tuple (k,v) representing the key and value of an item in priority queue P with minimum key (but do not remove the item); an error occurs if the priority queue is empty      |
| P.remove.min() | Remove an item with minimum key from priority queue P, and return a tuple (k, v), representing they key and value of the removed item; an error occurs if the priority queue is empty |
| P.is_empty()   | Return True if the priority queue P does not contain any items                                                                                                                        |
| len(P)         | Return the number of items in priority queue P                                                                                                                                        |

### (Binary) Heaps

Heaps are a type of tree, but typically stored in flat array
- **physically**: linear array
- **logically**: binary tree, filled on all levels except lowest
- each tree node corresponds to array element
- tree complete except lowest level, filled left to right

### Types of Heaps

**Max-Heap**:
- for every node excluding root, value is **at most** that of its parent: $A[parent[i]] \geq A[i]$.
- **largest** element stored at root

**Min-Heap**:
- for every node excluding root, value is **at least** that of its parent: $A[parent[i]] \leq A[i]$.
- **smallest** element stored at root

### Heap Properties

Binary tree with following properties:
- complete binary tree
- value stored at a node is greater or equal or lesser or equal to the values stored at the children depending on max- or min-heap

Heap represented as an array A has attributes:
- length(A): number of elements in array A
- heapSize(A): number of elements in heap stored in A

length(A) $\geq$ heapSize(A) at all times
- can be written as $A[v.parent.index] \geq A[v.index]$
- height of heap h: $\lfloor\log n \rfloor$. (floor of log n)

Building a heap:
1. when complete binary tree built, first node must be root
2. second node always left child of the root
3. third node is always right child of the root
4. next nodes always fill the next level from left to right

### Insertion into a Heap

To insert element into binary max-heap:
1. add new element node to bottom left H
2. if new node value bigger than parent, swap their values. set parent node as new node, go to step 2.
3. else exit

> [!tip] TIP
> Step 2 is called heapify.

For array indices:
- root is in $A[1]$ (array starting from $A[1]$)
- for index $i$, left($i$) = $A[2*i]$,
- right($i$) = $A[2*i+1]$
- parent($i$) = $A[i/2]$ (integer division, rounds down)

### Extracting Highest Priority

Heaps very good for storing priority queues and sorting
- given a sequence of objects with different priorities, want to deal with highest priority items first
- extract maximum element from collection

```HeapExtractMax(A)
def HeapExtractMax(A):
	ret = A[1] // biggest element (highest priority)
	A[1] = A[HeapSize(A)]
	HeapSize(A) = HeapSize(A) - 1
	Heapify(A,1,HeapSize(A))
	return ret
```

### Heapify

1. Starting at root, identify largest out of the current node $v$ and its children
2. Suppose largest element is in $w$.
3. If $w \neq v$
	1. swap $A[w]$ and $A[v]$.
	2. recurse into $w$ (contains now what root contained previously)

```Heapify
def Heapify(A,v,n):
	// n is heap size
	// find largest among v and 2v (left child)
	largest = v
	if 2v <= n and A[2v]>A[v]:
		then largest = 2v

	// find largest among winner above and 2v+1 (right child)
	if 2v+1 <= n and A[2v+1]>A[largest]:
		then largest = 2v+1

	if largest != v then
		swap A[v], A[largest]
		Heapify(A,largest,n)
```

Running time:
- time to fix node $i$ and its children = $\Theta(1)$
- recursion: T(size of subtree at largest)
- simplifies to $O(\log n)$

### BuildHeap

Converting a given array $A$ with $n$ arbitrary numbers into a heap
- start from leaves and build up from there

```BuildHeap
def BuildHeap(A,n):
	for i=n downto 1 do
		Heapify(A,i,n)
	endfor
```

Running time:
- Loose upper bound:
	- cost of Heapify call x no. of calls to maxHeapify
	- $O(\log n) \times O(n) = O(n \log n)$
- Tighter bound:
	- cost of a call to Heapify at a node depends on the height $h$ of the node - $O(h)$.
	- height of most nodes smaller than $n$.
	- height of nodes $h$ ranges from 1 to $\lfloor\log n\rfloor$.
	- no. of nodes of height $h$ is $\lceil n/2^h\rceil$.

$$T(n) = O\left(n\cdot\sum^{\log n}_{h=1}\frac{h}{2^h}\right) = O(n)$$

### Extraction (Deletion)

Element always deleted from root
- deleting element done in following steps:
	1. replace root's value with last node's value so that $H$ is still a complete binary tree but not necessarily a heap
	2. delete last node
	3. move down new root's value so that $H$ satisfies the heap property. Interchange root's value with largest child's value

### HeapSort

Call BuildHeap on unsorted data
- repeatedly call HeapExtractMin until empty

```HeapSort
def HeapSort(A):
	BuildHeap(A, Length(A))
	for i = Length(A) downto 2 do
		swap A[i] and A[1]
		HeapSize(A) = HeapSize(A) - 1
		Heapify(A, 1, HeapSize(A))
	endfor
```

Running time: $O(n) + n \cdot O(\log n) = O(n\log n)$

### Sorting Algorithms (Recap)

| algorithm     | running time (worst case) |
| ------------- | ------------------------- |
| SelectionSort | $O(n^2)$                  |
| InsertionSort | $O(n^2)$                  |
| MergeSort     | $O(n\log n)$              |
| QuickSort     | $O(n^2)$                  |
| BucketSort    | $O(n + K)$                |
| RadixSort     | $O(n\log K)$              |
| HeapSort      | $O(n\log n)$              |
- trade-offs involving, e.g, efficiency, memory usage, stability

> [!tip] NOTE:
> Most programming languages have a built-in sorting function: highly optimised combination of various algorithms.


