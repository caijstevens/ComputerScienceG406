#mcs 

### Inverse


> [!info] Definition
> The **inverse** of a function $f$ undoes the operation of $f$ and is written $f^{-1}$
- inverse has to be **unique** for $f^{-1}$ to be function (otherwise is a relation)
- when $f:X\rightarrow Y$ then $g$ is an inverse function of $f$ if $\forall x\in X . g(f(x)) = x$ and $\forall y\in Y.f(g(y)) = y$

### Inverse of a 2x2 Matrix

> [!todo] General Formula
> For a $2\times 2$ matrix $A$ where $$A=\begin{pmatrix} a & b \\ c & d\end{pmatrix}$$ The inverse is as follows: $$A^{-1}=\frac{1}{ad-bc}\begin{pmatrix} d & -b \\ -c & a\end{pmatrix}$$
- the inverse does not exist if $\det(A)=0$.

In general matrix multiplication is **not commutative**.
- but if $AB=I$ then: $$A=IA=(AB)A=A(BA)$$
- so $BA$ is also the identity and hence: $$AA^{-1}=A^{-1}A=I$$
### 2x2 Inverse with Gauss-Jordan

> [!success] Example
> $$\begin{pmatrix}1 & 2 \\ 3 & 4\end{pmatrix}$$
> Create a new matrix by combining the $2\times 2$ matrix with the identity matrix.
> $$\begin{pmatrix}1 & 2 & 1 & 0 \\ 3 & 4 & 0 & 1\end{pmatrix}\rightarrow\begin{pmatrix}1 & 2 & 1 & 0 \\ 0 & -2 & -3 & 1\end{pmatrix}$$
> Use Gauss-Jordan elimination.
> $$\rightarrow\begin{pmatrix}1 & 2 & 1 & 0 \\ 0 & 1 & \frac{3}{2} & -\frac{1}{2}\end{pmatrix}$$
> $$\rightarrow\begin{pmatrix}1 & 0 & -2 & 1 \\ 0 & 1 & \frac{3}{2} & -\frac{1}{2}\end{pmatrix}$$
> End result is the identity matrix followed by the inverse of the original matrix.

### Column Space and Column Rank

All vectors can be written as linear combinations of basis vectors.
- under a linear map $f:X\rightarrow Y, f(a\mathbf{x} + b\mathbf{y}) = af(\mathbf{x})+bf(\mathbf{y})$
- $f(X)$ is a span of the columns, called the **column space**.

> [!info] Definition
> The **column rank** is the dimension of the column space.
> Also the number of linearly independent columns.

### Row Rank

The **row space** is the span of all the row vectors.

> [!info] Definition
> The **row rank** is the dimension of the row space.
> Also the number of linearly independent rows.

### Row Rank = Column Rank

> [!info] Definition
> The **rank** of a matrix is the row/column rank.

> [!summary] Proof
> Each step of Gauss-Jordan elimination leaves column and row rank unchanged.
> Reduced row echelon form is reached.
> Can do more row/column operations to arrive at identity matrix surrounded by 0s.
> In this form row rank = column rank.
- dimension of $f(X)$ is the rank of the matrix for $f$.
- can calculate rank by Gaussian elimination
	- count non-zero rows in ref of non-augmented matrix
- matrix has **full rank** if the rank is as high as it can be (max row and column number)

### Kernel of a Linear Map

> [!info] Definition
> 
> If $f:X\rightarrow Y$ is a linear map:
> **Kernel** or **null space** of $f$ is the set of vectors that map to $\mathbf{0}$ i.e $$\{\mathbf{x}\in X.f(\mathbf{x})=0\}$$
- kernel forms a vector space - all linear combinations of kernel elements are in the kernel.

### No Inverse of Non-Square Matrices

Assume $f:X\rightarrow Y$. Can an inverse exist if $\dim(X) < \dim(Y)$?
- $\dim(f(X))\leq\dim(X)$, so $\dim(f(X)) < \dim(Y)$
- some elements of $Y$ are not in $f(X)$.
- therefore inverse cannot exist.

Can an inverse exist if $\dim(X) > \dim(Y)$?
- the columns of the matrix cannot be linearly independent
- there is non-zero vector that maps to zero (kernel non-trivial)
- any inverse cannot be unique because $f(\mathbf{x}+\mathbf{k}) = f(\mathbf{x})$ if $\mathbf{k}$ is in the kernel
- therefore inverse cannot exist.