#toc 

>[!info] Algorithm 
>A computational procedure taking values as input and producing values as output

>[!info] Problem 
>Specifies desired relationship between input/output

An algorithm is **correct** if for every input it halts with correct output
- a correct algorithm solves the problem

**Shortest path problem**: given graph $G$ and vertices $u,v,$ find shortest path from $u$ to $v$
- input instance: specific graph $G$ and vertices
- correct output: any path $P$ of $G$ from $u$ to $v$ such that no other path is shorter than $P$

### Insertion Sort 

Well-known algorithm for solving sorting problem 
```INSERTION-SORT(A)
for j <- 2 to n do
	key <- A[j]
	i <- j - 1
	while i > 0 and A[i] > key do
		A[i+1] <- A[i]
		i <- i - 1
	A[i+1] <- key
```
- scan left to right
- at every iteration $j$, $j-1$ previous items already sorted
- find place for $A[j]$ such that first $j$ items sorted

# Asymptotic Notation 

**Big-O**:
- $f(n) = O(g(n))$ if $\exists c > 0, n_0$ such that $f(n)\leq c\cdot g(n), \forall n\geq n_0$
**Big-Omega**:
- $f(n) = \Omega(g(n))$ if $\exists c > 0, n_0$ such that $f(n)\geq c\cdot g(n), \forall n\geq n_0$
**Theta**:
- $f(n)=\Theta(g(n))$ if $\exists c_1,c_2 > 0, n_0$ such that $c_1g(n)\leq f(n)\leq c_2g(n), \forall n\geq n_0$

**Little-o**:
- $f(n) = o(g(n))$ if for every $c_1 > 0, \exists n_0$ such that $f(n)\leq c_1g(n), \forall n\geq n_0$
**Little-omega**:
- $f(n) = \omega(g(n))$ if for every $c_2 > 0, \exists n_0$ such that $f(n)\geq c_2g(n), \forall n\geq n_0$

![[Screenshot 2025-10-09 at 16.32.39.png]]

# Running Time 

>[!info] Running Time 
>The **running time** $T(I)$ of an algorithm $\alpha$ on input $I$ is the time taken by $\alpha$ on $I$ until it halts. We classify inputs according to their size
- size is number of bits to represent input in real computer program