#toc 

# Master Method 

Depends on master theorem 
$$T(n)=aT(n/b)+f(n)$$
- for constants $a\geq 1, b>1$
- $f(n)$ is function on natural numbers

Outcomes:
1. If $f(n)=O(n^{\log_ba-\epsilon})$ for some $\epsilon>0$, then $T(n)=\Theta(n^{\log_ba})$
2. If $f(n)=\Theta(n^{\log_ba})$, then $T(n)=\Theta(n^{\log_ba}\cdot\log n)$
3. If $f(n)=\Omega(n^{\log_ba+\epsilon})$ for some constant $\epsilon>0$, and if $a\cdot f(n/b)\leq cf(n)$ for some constant $c<1$ and for sufficiently large $n$, then $T(n)=\Theta(f(n))$

# Multiplying Two Matrices 

Scenario:
- Input: two square matrices $A,B\in\mathbb{R}^{n\times n}$
- Output: their product $C\in\mathbb{R}^{n\times n}$
Can be done in time $\Theta(n^3)$ by using definition: $$c_{ij}=\sum\limits^n_{k=1}a_{ik}b_{kj}$$
### Divide and Conquer Approach 

Partition $A,B$ and $C$ into four parts (**block matrices**)

Example:
$$A=\begin{pmatrix}
A_{11} & A_{12} \\ A_{21} & A_{22}
\end{pmatrix},\space B=\begin{pmatrix}
B_{11} & B_{12} \\ B_{21} & B_{22}
\end{pmatrix},\space C=\begin{pmatrix}
C_{11} & C_{12} \\ C_{21} & C_{22}
\end{pmatrix}$$
Then: ![[Screenshot 2025-11-06 at 18.34.05.png]]
Runtime: 
- satisfies $T(n)=8T(n/2)+\Theta(n^2)$
- master theorem implies $T(n)=\Theta(n^3)$

# Strassen's Algorithm 

1. Divide $A,B$ and $C$ into four parts as before
	- Running time: $\Theta(1)$
2. Create 10 auxiliary matrices $S_1,\dots,S_{10}\in\mathbb{R}^{n/2\times n/2}$ obtained by sums or differences of $A_{11},\dots,B_{22}$
	- Running time: $\Theta(n^2)$
3. Using all matrices, recursively compute 7 product matrices $P_1,\dots,P_7\in\mathbb{R}^{n/2\times n/2}$ 
	- Running time: $7T(n/2)$
4. Compute $C_{11},\dots,C_{22}$ by adding/subtracting combinations of $P_1,\dots,P_7$
	- Running time: $\Theta(n^2)$

Worse case running time: $$T(n)\leq7T(n/2)+\Theta(n^2)$$
Therefore we obtain: $$T(n)=\Theta(n^{\log_27})=\Theta(n^{2.8074})$$

