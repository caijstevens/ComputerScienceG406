#mcs 

### Systems of Linear equations

> [!info] Definition
> A **linear equation** in $n$ variables $x_1,\dots,x_n$ is an equation of the form $$a_1x_1+a_2x_2+\dots+a_nx_n=b$$ where $a_i$ and $b$ are constants.
- a finite set of linear equations is called a **system of linear equations** (or **linear system**).
- a general linear system can be written as $$a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n = b_1$$$$a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n = b_2$$$$\vdots = \vdots$$$$a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=b_m$$
- a solution to this system is a sequence of $s_1,\dots,s_n$ of numbers such that $x_1=s_1,\dots,x_n=s_n$ satisfies every equation.
- linear system is **consistent** if has at least one solution, **inconsistent** if not.

> [!summary] Example: One Solution
> Solve linear system $$x-y=1$$$$2x+y=6$$
> Eliminate $x$ from 2nd equation by adding $-2$ times the 1st equation to the 2nd. $$x-y=1$$$$3y=4$$
> We have $y=\frac{4}{3}$, and from the 1st equation $x=\frac{7}{3}.$ System has one solution.

> [!summary] Example: No Solutions
> Solve linear system $$x+y=4$$$$3x+3y=6$$
> Eliminate $x$ from 2nd equation by adding $-3$ times the 1st equation to the 2nd. $$x+y=4$$$$0=-6$$
> The 2nd equation is contradictory. System has no solutions.
> 

> [!summary] Example: Infinite Solutions
> Solve linear system $$4x-2y=1$$$$8x-4y=2$$
> Eliminate $x$ from 2nd equation by adding $-3$ times 1st equation to the 2nd. $$4x-2y=1$$$$0=0$$
> The 2nd equation imposes no restrictions on $x$ and $y$, can be omitted.
> Solving for $x$, we get $x=\frac{1}{4}+\frac{1}{2}y.$
> Solution set can be described as set of all pairs of numbers of the form $\frac{1}{4}+\frac{1}{2}y,y$. System has infinitely many solutions.

A linear system can be written in matrix form $A\mathbf{x}=\mathbf{b}$ where $$A=\begin{pmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn}\end{pmatrix}, \space\mathbf{x}=\begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n\end{pmatrix}\space\text{ and } \mathbf{b}=\begin{pmatrix} b_1 \\ b_2 \\ \vdots \\ b_m\end{pmatrix}$$
- the matrix $A$ is called the **coefficient matrix** of the system
- if $A$ is square and invertible then the solution can be found as $\mathbf{x}=A^{-1}\mathbf{b}.$

### Augmented Matrix and Elementary Row Operations

The **augmented matrix** of a linear system is the matrix $$(A|\mathbf{b})=\begin{pmatrix}a_{11} & a_{12} & \cdots & a_{1n} \space\vert & b_1\\ a_{21} & a_{22} & \cdots & a_{2n} \space\vert & b_2\\ \vdots & \vdots & \ddots & \vdots \space\space\space\space\space\vert & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn}\space\vert & b_m\end{pmatrix}$$
Augmented matrix **elementary row operations**:
1. Multiply a row through by a non-zero constant
2. Interchange two rows
3. Add a constant times one row to another

### Row Echelon Form

If matrix of linear system in variables $x,y,z$ is in form $$\begin{pmatrix}1 & 0 & 0 \space\vert & 1\\ 0 & 1 & 0 \space\vert & 2 \\ 0 & 0 & 1\space\vert & 3\end{pmatrix}$$ Then we know the solution: $x=1, y=2, z=3$.

Matrix is in **row echelon form** if has following properties:
- if row is not all 0s, first non-zero number is 1.
- rows that are all 0s are grouped together at bottom
- if two successive rows not all 0s, leading 1 of higher row occurs further left than leading 1 of lower row.

Matrix is in **reduced ref** if it is in ref, plus:
- each column that contains a leading 1 has 0s everywhere else.

Finding solution numbers from (r)ref:
- if row has leading 1 in **last** column, system has **no solutions**.
- if number of leading 1s = number of variables (and no leading 1 in last column), system has **one unique solution**.
- If number of leading 1s smaller than number of variables (and no leading 1 in last column), system has **infinite solutions**.

### Gaussian Elimination

**Goal**: Transform a matrix to row echelon form by using row operations.

> [!success] Method (+ Example)
> 1. Locate the **pivot column** (leftmost column containing a non-zero) $$\begin{pmatrix} 0 & 0 & -2 & 0 & 7 & 12 \\ 2 & 4 & -10 & 6 & 12 & 28 \\ 2 & 4 & -5 & 6 & -5 & -1\end{pmatrix}$$
> 2. Choose a **pivot** - a non-zero in pivot column, and interchange first row with another row (if necessary) to move pivot to the top in this column $$\begin{pmatrix} 2 & 4 & -10 & 6 & 12 & 28 \\ 0 & 0 & -2 & 0 & 7 & 12 \\ 2 & 4 & -5 & 6 & -5 & -1\end{pmatrix}$$
> 3. If $a$ is the pivot, multiply the first row by $1/a$ to get a leading $1$. $$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & -2 & 0 & 7 & 12 \\ 2 & 4 & -5 & 6 & -5 & -1\end{pmatrix}$$
> 4. Add suitable multiples of the first row to the rows below so that all numbers below the leading $1$ are $0$s.$$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & -2 & 0 & 7 & 12 \\ 0 & 0 & 5 & 0 & -17 & -29\end{pmatrix}$$
> 5. Separate the top row from the rest and repeat steps 1-5 for the matrix below the line. $$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ \hline & \hline & \hline & \hline & \hline & \hline \\ 0 & 0 & -2 & 0 & 7 & 12 \\ 0 & 0 & 5 & 0 & -17 & -29\end{pmatrix}$$
> 6. Repetitions: $$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ \hline & \hline & \hline & \hline & \hline & \hline \\ 0 & 0 & 1 & 0 & -7/2 & -6 \\ 0 & 0 & 5 & 0 & -17 & -29\end{pmatrix}$$$$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & 1 & 0 & -7/2 & -6 \\ \hline & \hline & \hline & \hline & \hline & \hline \\ 0 & 0 & 0 & 0 & 1/2 & 1\end{pmatrix}$$$$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & 1 & 0 & -7/2 & -6 \\ 0 & 0 & 0 & 0 & 1 & 2\end{pmatrix}$$
>    The last matrix is in ref, the output of Gaussian elimination.

### Gauss-Jordan Elimination

Same as Gaussian elimination, but the end result is in **reduced row echelon form**.

> [!success] Continued Method (+ Example)
> $$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & 1 & 0 & -7/2 & -6 \\ 0 & 0 & 0 & 0 & 1 & 2\end{pmatrix}$$
> 6. Beginning from the last non-$0$ row and working upward, add suitable multiples of each row to create $0$s above the leading $1$s.
> $$\begin{pmatrix} 1 & 2 & -5 & 3 & 6 & 14 \\ 0 & 0 & 1 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 1 & 2\end{pmatrix}$$$$\begin{pmatrix} 1 & 2 & -5 & 3 & 0 & 2 \\ 0 & 0 & 1 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 1 & 2\end{pmatrix}$$$$\begin{pmatrix} 1 & 2 & 0 & 3 & 0 & 7 \\ 0 & 0 & 1 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 1 & 2\end{pmatrix}$$

### Homogeneous Linear Systems

A linear system $A\mathbf{x}=\mathbf{b}$ is homogeneous if $\mathbf{b}$ is all $0$s.
- such a system has a **trivial solution**: $\mathbf{x}$ is all $0$s. Any other solution is called **non-trivial**.

> [!info] Theorem
> If a homogeneous linear system has $n$ variables and the rref of its augmented matrix has $r$ non-$0$ rows, then the system has $n-r$ free variables.
> 
- being consistent and having free variables implies having infinitely many solutions.

> [!error] Corollary
> A homogeneous linear system with more variables than equations has infinitely many solutions.
