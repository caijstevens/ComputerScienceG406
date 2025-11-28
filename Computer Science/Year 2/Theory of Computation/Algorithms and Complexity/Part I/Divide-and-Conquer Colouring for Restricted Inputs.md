 #toc 

For recursive algorithms:
- **divide** problem into subproblems
- **conquer** subproblems by solving (recursive/straightforward)
- **combine** solutions into solution for main problem

Natural way to calculate runtime: **recurrence relations**
- inequalities describing function via same function on small inputs
![[Screenshot 2025-10-23 at 16.11.47.png]]
- this is true for binary search, becomes $T(n)=\Theta(\log n)$

# Colouring 

**Colouring** of graph is assigning colours to vertices such that two adjacent vertices have different colours.
- colouring with $k$ different colours is a $k$-colouring
- **chromatic number** $\chi_G$ is smallest $k$ value for which graph has $k$-colouring 
- an NP-hard problem

# Dealing with NP-hardness 

Options:
- heuristics
- approximation algorithms
- exact algorithms 
- parameterised algorithms
- algorithms for restricted inputs 
	- exploit structure of input to develop faster algorithms

# Cographs

>[!info] Cograph
>Let $G_1$ and $G_2$ be two vertex-disjointed graphs 
>The **disjoint union** $G_1+G_2$ has:
>- vertex set $V(G_1)\cup V(G_2)$
>- edge set $E(G_1)\cup E(G_2)$
>  
>The join $G_1\times G_2$ has:
>- vertex set $V(G_1)\cup V(G_2)$
>- edge set $E(G_1)\cup E(G_2)\cup E^*$ where $E^*$ is the set of all edges between each set's vertices

A graph is a **cograph** if it can be created using these rules:
1. The 1-vertex graph is a cograph
2. If $G_1$ and $G_2$ are cographs, then so is $G_1+G_2$
3. If $G_1$ and $G_2$ are cographs, then so is $G_1\times G_2$

### Cographs: $P_4$ Theory 

Let $P_4$ denote path on 4-vertices 
- graph $G$ contains $P_4$ as **induced subgraph** if $G$ can be modified to $P_4$ via vertex deletions (4 vertices connected in chain, no cycle)
- if not, graph is $P_4$-free

>[!info] Theorem 
>A graph $G$ is a **cograph** $\iff G$ is $P_4$-free
>

### Cotree

Let $G$ be a cograph. The **cotree** $T_G$ of $G$ is the unique decomp tree where:
1. The root $r$ of the tree represents the graph $G_r=G$
2. Every leaf $x$ of the tree represents exactly one vertex of $G$ and vice versa
3. Every internal node $x$ of the tree has at least 2 children labelled $+$ or $\times$, represents induced subgraph $G_x$ where:
	- if $x$ is $+$-node, $G_x$ is disjoint union of all graphs $G_y$ where $y$ is a child of $x$
	- if $x$ is a $\times$-node, $G_x$ is the join of all graphs $G_y$ where $y$ is a child of $x$
4. Along path from root $r$ to any leaf, labels of internal nodes **alternate** between $+$ and $\times$

>[!info] Theorem 
>Any cograph $G$ has a **unique cotree**. However if condition 4 dropped, there can be many trees representing $G$.

# Colouring Algorithm for Cographs

For cograph $G$, construct cotree $T_G$.
- can be done in $O(n+m)$ time

Follow **bottom-up** approach: process $x$ after processing its children
- **leaves**: each leaf represents single vertex of $G$. Chromatic number of single-vertex graph is 1.
- **union-nodes**: if $x$ is a $+$-node, $\chi_{G_x}$ is the maximum of the chromatic numbers of the graphs $G_y$ where $y$ is a child of $x$.
- **join-nodes**: if $y$ is a $\times$-node, then $\chi_{G_x}$ is the sum of the chromatic numbers of the graphs $G_y$ where $y$ is a child of $x$

Therefore root processed last, represents the graph $G_r=G$
- as number of $T$ is $O(n)$ and we used $O(n)$ time per node, total runtime is **polynomial**

# Maximum-Subarray Problem 

"Buy low, sell high"
- polynomial time
- brute-force all pairs $i,j$ of days, check price difference, keep largest 
- running time $\binom{n}{2}=\Theta(n^2)$
- looking for contiguous sub-array of array with largest sum

Divide and conquer approach:
- every contiguous subarray is either:
	1. entirely in $A[1\dots mid]$
	2. entirely in $A[mid+1\dots n]$
	3. crossing midpoint such that $1\leq i\leq mid<j\leq n$
- cases 1 and 2 solved recursively

Finding max subarray that crosses midpoint:
- not smaller instance
- can be computed in $O(n$)

Runtime analysis:
![[Screenshot 2025-10-23 at 16.56.22.png]]
- same as merge sort
- $= T(n) = \Theta(n\log n)$


# Another Application 

Given array of $n$ numbers, already know:
- can compute max or min number with $n-1$ comparisons 
- can find max **and** min number with $2n-2$ comparisons