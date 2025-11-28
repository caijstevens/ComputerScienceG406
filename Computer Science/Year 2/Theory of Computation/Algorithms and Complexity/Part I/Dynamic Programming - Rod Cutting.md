#toc 

# Rod Cutting Problem 

Determining best way to cut steel rods to maximise profit.
- for $i=1,\dots,n$ the price $p_i$ is known for a rod of length $i$cm.
- determine maximum revenue $r_n$ obtained by cutting up road and selling pieces.

An integer partition of positive integer $n$ is a list of positive integers $<a_1,\dots,a_k>$ such that $a_1\leq a_2\leq\dots\leq a_k$ and $$\sum\limits^k_{i=1}a_i=n$$
Let $p(n)$ denote number of integer partitions of $n$, then $$p(1)=1,\space p(2)=2,\space p(3)=3, \space p(4)=5\dots$$
Proved theorem for brute force time: $$p(n)\sim\frac{1}{4n\sqrt{3}}\exp(\pi\sqrt\frac{2n}{3})$$
- therefore brute force has **exponential** runtime.

# Dynamic Programming 

For all $n\geq 1$: $$r_n=\max\{p_i+r_{n-i}:1\leq i\leq n\}$$
- $p_n$ corresponds to no cuts and $p_i+r_{n-i}$ to cutting into a rod of length $i$ and another rod of length $n-i$
- solve recursively using backtracking to find optimal solution 
- runtime still exponential 

### More Optimal Method 

**Dynamic Programming** uses additional memory to save computation time
- time-memory trade-off 

Runs in polynomial time when:
- polynomial number of distinct subproblems 
- each subproblem solvable in polynomial time 

>[!important] Tip!
>For every algorithm that uses subproblems, subproblems have to be **independent**!

Two subproblems independent if:
- they don't share resources 
- solution to one subproblem does not affect solution to another subproblem 

Why does it work?:
- optimal substructure 
- no overlapping subproblems 

**Memoization** prevents overlap, store output once and keep reusing.

# Top Down Vs Bottom Up 

### Top Down 

1. Write procedure recursively in natural manner 
2. Modify to save each subproblem result 
3. Procedure checks if subproblem solved previously 
4. If not, procedure computes value in usual manner

### Bottom Up 

Depends on idea of size of subproblem 
1. Sort subproblems by size
2. Solve in size order
3. Solve each subproblem only once. When we first see it, all prerequisite subproblems already solved.

Both top-down and bottom-up have worst case runtime of $\Theta(n^2)$
- usually both have same complexity
- bottom-up has lower constants due to less overhead for procedure calls 
- sometimes top-down does not actually recurse to solve all subproblems 