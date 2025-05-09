#ads 
### Sorting and Decision Trees

**Decision tree** is a **full** binary tree
- every node has either zero or two children
- represents comparisons between elements performed by particular algorithm run on particular input
- only comparisons relevant, everything else is ignored

**Internal nodes** labelled $i \space\colon j$ for $1 \leq i, j \leq n$, so elements $i$ and $j$ compared
- **downward edges** labelled "$\leq$" or ">" depending on comparison outcome
- **leaves** labelled with some permutation of $\{1, \dots , n\}$
- **branch** from root to lead describes comparison sequence (nodes and edges) and ends in some resulting sequence (leaf)
- at least $n!$ leaves

Decision tree for SelectionSort (3-element input):![[Screenshot 2025-04-25 at 19.22.15.png]]
- $3! = 6$ possible input permutations, therefore at least 6 leaves

### Lower Bound for Worst Case
For given $n$, lower bound on heights of **all** decision trees is lower bound on running time of comparison based sort algorithm.


> [!info] Theorem
> Any comparison-based sorting algorithm requires $\Omega(n\log n)$ comparisons in the worst case.

> [!summary] Proof
> 
> - sufficient to determine minimum height of a decision tree in which each permutation appears as leaf
> - consider decision tree of height $h$ with $\ell$ leaves corresponding to a comparison sort on $n$ elements
> - each of the $n!$ permutations of input appears as some leaf: $\ell\geq n!$
> - binary tree of height $h$ has at most $2^h$ leaves: $\ell\leq 2^h$
> - together: $n! \leq \ell \leq 2^h$ and therefore, $n! \leq 2^h$
> - takes log: $h \geq \log(n!) = \Omega(n\log n)$

### Selection and Adversaries

**Adversary** is second algorithm intercepting access to input
- gives answers so always consistent input
- ensures original algorithm has **insufficient info** for **maximum time**
	- aka dynamically constructs bad input
- doesn't know what original algorithm will do in future
	- must work for **any** original algorithm

### Example: Finding Max

Goal: to find max element in unsorted array
- in array of size $n$, can do this with $n-1$ comparisons

> [!info] Theorem
> Any comparison-based algorithm for this problem requires at least $n-1$ comparisons in the worst case

> [!summary] Proof
> After $\leq n-2$ comparisons, $\geq 2$ elements never lost in a comparison
> 	- therefore adversary can make any of those max and be consistent
> 	- not enough info for algorithm to make a decision
> 	- therefore algorithm needs to make at least $n-1$ comparisons

The only relevant algorithm info is how many elements lost the $(\geq 1)$ comparison
- as soon as $n-1$ elements lost, algorithm can find that max is the one that has never lost
- assume each index $i$ has status: $N$ (never lost) or $L$ (lost), initially all have $N$.
- **adversary's goal:** delay changing $N \rightarrow L$ as much as possible

**adversary's strategy** can be represented as status update table
- shows number of bits of new relevant info
- when algorithm asks to compare $i\space\colon j$, reply as follows:

| status for $i\space\colon j$ | adv reply   | new status | new info |
| ---------------------------- | ----------- | ---------- | -------- |
| $N;N$                        | $a_i > a_j$ | $N;L$      | 1        |
| $N;L$                        | $a_i > a_j$ | No Change  | 0        |
| $L;N$                        | $a_i < a_j$ | No Change  | 0        |
| $L;L$                        | Consistent  | No Change  | 0        |
One comparison gives $\leq 1$ bit of new relevant info (e.g. new L)
- algorithm needs $n-1$ bits of info to make decision
- therefore $\geq n-1$ comparisons needed

### Example: Finding 2nd Largest

Goal: to find 2nd largest element in an unsorted array

> [!info] Theorem
> Any comparison-based algorithm for this problem requires at least $n + \lceil\log_2(n)\rceil - 2$ comparisons in the worst case.

Observations:
- correct algorithm must also determine max
- $n-1$ elements must lose 1 comparisons
- 2nd largest must lose to max directly
- if max had direct comps with $m$ elements, then $m-1$ elements must lose 2 comparisons
- therefore required comps $\geq (n-1) + (m-1) = n + m - 2$ comparisons

**This proves that the adversary can force $\lceil\log_2n\rceil$ comparisons involving max**
- adversary assigns weight $w_i$ to each input element $a_i$
- initially all $w_i = 1$, then update using following:

| weights         | adv reply   | update                     |
| --------------- | ----------- | -------------------------- |
| $w_i > w_j$     | $a_i > a_j$ | $w_i = w_i + w_j, w_j = 0$ |
| $w_i < w_j$     | $a_i < a_j$ | $w_j = w_i + w_j, w_i = 0$ |
| $w_i = w_j > 0$ | $a_i > a_j$ | $w_i = w_i + w_j, w_j = 0$ |
| $w_i = w_j = 0$ | Consistent  | No change                  |
Analysis:
- $w_i = 0 \iff i$ lost $\geq 1$ comparison
- weight of an element at most doubles after comparison
- if max is involved in $m$ comparisons, weight is $\leq 2^m$
- in the end, max accumulates all weight, so $n \leq 2^m$
- taking logs, $\log_2n\leq m$ as required
- therefore adversary can force $\lceil\log_2n\rceil$ comparisons with max, proving theorem

### Finding $k$th Largest

Let $V(n,k)$ be the number of comparisons necessary and sufficient to find $k$th largest in any array of size $n$
- exact value of $V(n,k)$ known for $k = 1, 2, n-1, n$.
- for other values of $k$, only some bounds are known

> [!info] Theorem
> For all $1\leq k\leq n$, it holds that $V(n,k)\geq n-k + \lceil\log_2(\frac{n}{k-1})\rceil$.


