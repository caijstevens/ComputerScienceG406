#ads 

For any **comparison-based** sorting algorithm A and any $n \in \mathbb{N}$ large enough there exists an input of length n that requires A to perform $\Omega (n \log n)$ comparisons.
- no such algorithm can ever consistently beat stated bound

### BucketSort
Premise:
- Start with k empty buckets numbered 0 to k-1.
- Scan the list and place element s[i] in bucket s[i] and then output the buckets in order
- will need array of buckets, and values in list to be sorted will be indexes to buckets
- no comparisons necessary

![[Screenshot 2025-04-20 at 16.20.02.png]]

Each bucket is just counter which is incremented whenever a value matching the bucket's number is encountered.
- if sorting according to keys, each bucket is queue
	- entries enqueued into matching bucket
	- entries dequeued back into array after scan

**time complexity:**
- bucket initialisation: $O(k)$
- from array to buckets: $O(n)$
- from buckets to array: $O(n)$
- overall worst case: $O(n + k)$

if k is small (e.g $o(n \log n)$), overall running time of bucket sort is $o(n \log n)$.
- therefore beating lower bound from theorem
- (because theorem doesn't apply - not comparison-based)
- if k gets really large then running time can be worse than that of any other algorithm so far

### RadixSort

Have as many buckets as you have different digits (e.g max 10 for base-10)
- if max value 999999, only 10 buckets necessary (unlike 1 million for bucketsort)
- repeatedly bucketsort by given digit
- number of rounds will depend on values but number of buckets only depends on number of different digits

RadixSort works if the BucketSort phases are stable.
- work done in previous rounds isn't being destroyed
	- if two elements with same first digit, first appearing element in prior array will be first appearing in resulting array
- if fixed number **d** of bucket sort stages, then radix sort is $O(dn)$.
	- **d** bucket sort stages each taking $O(n)$ time.

**overall time complexity** is $O(dn)$ where **d** is the number of digits

comparing to bucketsort for range $\{0,...,k-1\}$ :
- radix sort: $d = \log_{10}(k)$ therefore $O(n \log k)$.
- bucket sort: $O(n + K)$.
- faster algorithm depends on the value of k:
	- $K = n \rightarrow$ bucket sort wins
	- $K = n^2 \rightarrow$  radix sort wins
	- $K = 2^n \rightarrow$ radix sort
	- if K is constant then both are linear time $(\Theta(n))$.

### Searching and Selecting

Given $n$ numbers in array $A[1 \dots n]$ in sorted order and pairwise distinct (all values unique)
- also given number $x$ equal to one of the $n$ numbers above
- goal is to devise algorithm to find position of $x$ in $A$.
- trivial solution is just to scan left to right until found

### Binary Search

Peek into middle of given array at position $p = n/2$
- if $A[p] = x$ then lucky and done, return $p$.
- if $x > A[p]$, focus search on right of $A[p]$ and ignore left (opposite if smaller)
- can be recursive with call search($A,1,n,x$) followed by call search($A,p+1,n,x$) if bigger, or call search($A, 1, p-1, x$) if smaller.

Called binary search because each unsuccessful step at least halves search space
- divide and conquer
- has recurrence $T(n) = T(n/2) + O(1) = O(\log n)$
- much quicker than linear search for large $n$.

### Selection

If input is unsorted and looking for value of i-th smallest element, this is a **selection** problem

### QuickSelect

Similar idea to QuickSort, recursive and uses partition() function for selecting pivot and partitioning into LOW and HIGH
- only one recursive call to sort
- after partitioning, pivot is in correct position overall
- just compare pivot position after partitioning with sought index $i$.

```
QuickSelect(int A[1...n], int left, int right, int i)::

if (left == right) then
	return A[left]
else
	pivot = Partition(A, left, right)
	if (i == pivot) then
		return A[i]
	else if (i < pivot) then
		return QuickSelect(A, left, pivot-1, i)
	else
		return QuickSelect(A, pivot+1, right, i)
	end if
end if
```

QuickSelect performance:
- Can be a lot slower than other algorithms if pivots are poorly chosen
- but if pivot chosen at random, expected runtime of $O(n)$, very good

### Median-of-Medians

QuickSelect with a good strategy for choosing pivots.
- doubly recursive
- guaranteed linear time

Algorithm Select($i, n$):
1. Divide $n$ elements into groups of 5. Find median of each 5-element group
2. Recursively select median $x$ of the $n/5$ group medians to be the pivot.
3. Partition around the pivot $x$. Let $k = rank(x)$
	Then:
	```
	if i = k then return x
	else if i < k
		then recursively Select the ith smallest element in the lower part
	else recursively Select the (i-k)th smallest element in the upper part
	```

Analysis:
- at least 3 of the $n/10$ elements are $\leq x \implies$ at most $n-3$ of the $n/10$ elements are $\geq x$
- at least 3 of the $n/10$ elements are $\geq x \implies$ at most $n-3$ of the $n/10$ elements are $\leq x$.
- recursive Select call executed on at most $n-3$ of the $n/10$ elements

QuickSelect gives the following recurrence: $$T(n) = T\left(\frac{1}{5}n\right) + T\left(\frac{7}{10}n + 3\right) + n$$
To show: $T(k) \leq ck$ for all $k < n, n > 0$:
$$
T(n) \leq c(n/5) + c(7n/10+3) + n
$$
$$\leq cn/5 + 3cn/4 + n$$
$$=19cn/20+n$$
$$\leq cn - (cn/20-n)$$
leads to: $$T(n) \leq cn$$
QuickSelect vs MoM:
- QS singly recursive $\rightarrow$ less work in each iteration than MoM
- QS can have more iterations than MoM
- Randomised QS often used because bad behaviour rare
- MoM when guaranteed good behaviour absolutely needed