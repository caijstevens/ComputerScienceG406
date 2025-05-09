#ads 

### Insertion Sort (Non-Recursive)

When j has a certain value, it inserts the j-th element into already sorted sequence $a_1,...,a_{j-1}$.
- can be proved correct by using invariant "after j-th iteration first j + 1 elements are in order"
- running time between $n-1$ and $\frac{n(n-1)}{2}$ - worst case $O(n^2)$. 

### Selection Sort (Non-Recursive)

**Invariant**: after i-th iteration positions $1,...,i$ contain the overall i many smallest elements in order.
- **elem**: keeps track of current idea of **value** i-th smallest element
- **pos**: keeps track of idea of **position** of i-th smallest element

Time complexity: $O(n^2)$ 

### Bubble Sort (Non-Recursive)

**Invariant**: after the iteration for i of the outer for-loop, positions $i,...,n$ contain the overall $n - i + 1$ many largest elements in order.

**Time complexity**: $(n-1) + (n-2)  + ... + 2 + 1 = O(n^2)$.

**Variation**: Terminate if no swap executed during inner for-loop.

### Merge Sort (Recursive)

Basic idea:
- if given sequence of no more than one element then done
- otherwise (length > 1): split sequence into two shorter sequences of equal length, sort recursively, and merge two resulting sequences

Merge sort is probably simplest recursive sorting algorithm
- bad cases much less bad than other algorithms
- but good cases may be worse than others

**Time complexity** is always around $n \log(n)$
- (much better than $n^2$)

### QuickSort (Recursive)

Divide and conquer algorithm
- split input into two parts
- recursively sort them, one after the other
- **concatenate** resulting, sorted subsequences

At beginning of each recursive call, QuickSort picks one element from current sequence: pivot
- partitioning done with regard to pivot
- each element smaller than pivot goes into left part, bigger into right part
- parts may have very different sizes

QuickSort does the difficult parts before recursing, allowing for simple concatenation
- MergeSort does the merging after the recursive calls hence why it is a bit less efficient