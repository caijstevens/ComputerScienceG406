#mcs 

### Basis Representation

> [!warning] Reminder
> A set of vectors is a **basis** for the vector space if it spans the whole space and is linearly independent.

> [!info] Theorem
> For a vector space $V$, the representation of any $\mathbf{v}\in V$ as a linear combination of a given basis $S = \{\mathbf{s_1},\dots,\mathbf{s_n}\}$ is unique.

> [!summary] Proof
> 1. Assume two representations of $\mathbf{v}$ such that: $$\mathbf{v}=\alpha_1s_1+\alpha_2s_2+\cdots+\alpha_ns_n$$ and $$\mathbf{v}=\beta_1s_1+\beta_2s_2+\cdots+\beta_ns_n$$ where $\alpha_{1,2,\dots,n}$ and $\beta_{1,2,\dots,n}$ are scalars.
> 2. Subtract the two representations: $$\mathbf{v}-\mathbf{v}=(\alpha_1s_1+\alpha_2s_2+\cdots+\alpha_ns_n)-(\beta_1s_1+\beta_2s_2+\cdots+\beta_ns_n)$$ This simplifies to: $$0=(\alpha_1-\beta_1)s_1+(\alpha_2-\beta_2)s_2+\cdots+(\alpha_n-\beta_n)s_n$$
> 3. Use the linear independence of the basis: since $S = \{\mathbf{s_1},\dots,\mathbf{s_n}\}$ is a **linearly independent** set, the only way the linear combination of these basis vectors can sum to zero is if each scalar in the combination is zero. Therefore: $$\alpha_1-\beta_1=0,\space\space\alpha_2-\beta_2=0,\space\space\dots,\space\space\alpha_n-\beta_n=0$$ This gives us: $$\alpha_1=\beta_1,\space\space\alpha_2=\beta_2,\space\space\dots,\space\space\alpha_n=\beta_n$$
> 4. **Conclusion**: Since $\alpha_i=\beta_i$ for all $i=1,2,\dots,n$, the two linear combinations are identical. Thus, the representation of $\mathbf{v}$ as a linear combination of the basis vectors is unique.


### Canonical (standard) Basis

> [!info] Definition
> The **canonical basis** is the most natural and commonly used basis for a vector space. For the space $\mathbb{R}^n$, the canonical basis is: $$\{e_1,e_2,\dots,e_n\}$$ where $$e_i=(0,0,\dots,1,\dots,0)$$ i.e. the 1 in the $i$-th position and zeros elsewhere.
- made of vectors that "pick out" each coordinate one at a time.

Example:
- in $\mathbb{R}^2$, $e_1=(1,0),\space e_2=(0,1)$
- every vector $(x,y)$ can be written as: $$xe_1+ye_2=x(1,0)+y(0,1)$$
- in 3D sometimes referred to as $\mathbf{e}_x,\mathbf{e}_y,\mathbf{e}_z$ or $\mathbf{i},\mathbf{j},\mathbf{k}$.

### Linear Map

> [!info] Definition
> If we have a function $f:V\rightarrow W$ where $V$ and $W$ are vector spaces over a field $F$ then $f$ is a **linear map** if for any vectors $\mathbf{u}, \mathbf{v}\in V$ and $a\in F$, we have **Additivity**:: $$f(\mathbf{u}+\mathbf{v})=f(\mathbf{u})+f(\mathbf{v})$$ and **Homogeneity** (scalar compatibility):
> $$f(a\mathbf{v})=af(\mathbf{v})$$
- transforms vectors from one space to another without changing linear structure.
- respects linear combinations
- sometimes called **linear transformations** or **vector space homomorphisms**.
- if $V=W$ then $f$ is an **endomorphism**.
- all linear maps preserve lines.

Examples of linear maps:
- scaling (on $\mathbb{R}^3$).
- reflection
- rotation
- shearing
	- sliding one part of a space over another without changing areas, lengths along one axis or parallelism, e.g. a horizontal shear: $T(x,y)=(x+ky,y)$ where $k$ is the shear factor.
- projection
	- drops vectors onto a subspace where, once applied, applying the projection again doesn't move them, so $P:V\rightarrow V$ is a **projection** if $P^2=P$.
- embedding
	- an embedding is a map $f:V\rightarrow W$ between vector spaces where:
		- $V$ is a lower-dimensional space
		- $W$ is a bigger space
		- $f$ is **injective** (one to one) and preserves linear structure
		- e.g. $f: \mathbb{R}^2\rightarrow\mathbb{R}^3,\space f(x,y)=(x,y,0)$
- differentiation (on polynomials)

Every vector $\mathbf{v}$ can be represented as a linear combination of basis vectors, $\mathbf{s}_i\in S$. If we apply a linear map $f$ then $$f(\mathbf{v})=f(\sum^{n}_{i=1}a_i\mathbf{s}_i)$$ $$=\sum^{n}_{i=1}a_if(\mathbf{s}_i)$$
### Images of Basis Vectors

> [!info] Definition
> The **image** of a basis vector $b_i$ from a basis $\{b_1,b_2,\dots,b_n\}$ of $V$ under $T$ is: $$T(b_i),$$ where $T:V\rightarrow W$ is a **linear map** between two vector spaces. The image is the result of applying linear map $T$ to the single basis vector.

Example - rotation 90 degrees anti-clockwise in $\mathbb{R}^2$
- Q: What are the images of the canonical basis vectors $\mathbf{e}_1(1,0)$ and $\mathbf{e}_2(0,1)$?
- A: $(0,1)$ and $(-1,0)$ or $\mathbf{e}_2$ and $-1\mathbf{e}_1$
- Turn these into column vectors to get matrix representation $$\begin{pmatrix} 0 & -1 \\ 1 & 0\end{pmatrix}$$
What happens when rotating vector $(2,3)$?
$$rotate((2,3))=rotate(2\mathbf{e}_1+3\mathbf{e}_2)$$$$=2.rotate(\mathbf{e}_1)+3.rotate(\mathbf{e}_2)$$
$$=2\mathbf{e}_2+3.(-1.\mathbf{e}_1)$$
$$=(-3,2)$$
### Generalising Basis Images

Can write basis vector images columns under $f$ as a matrix: $$\begin{pmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn}\end{pmatrix}$$
- $a_{ij}$ is $i$th component of $f$-image of $j$th basis vector $$f(\mathbf{e}_j)=\sum^{m}_{i=1}a_{ij}\mathbf{e}_i$$
- image of vector $A\mathbf{x}=A(x_1,\dots,x_n)$ is $$f ( \sum_{j=1}^n x_j \mathbf{e}_j) = (\sum_{j=1}^n x_j f(\mathbf{e}_j))$$$$=(\sum_{j=1}^n x_j \sum^{m}_{i=1}a_{ij}\mathbf{e}_i)$$$$=\sum^{n}_{j=1}\sum^{m}_{i=1}a_{ij}x_j\mathbf{e}_i$$
- so the ith component of the image of $\mathbf{x}$ is $\sum^{m}_{j=1}a_{ij}x_j$

### Identity Matrix

All basis vectors map to themselves via identity matrix $I$ $$I=\begin{pmatrix} 1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & 1\end{pmatrix}$$
- $I$ is a diagonal matrix: $i\neq j \Rightarrow a_{ij}=0$

### Combining Linear Maps

Suppose we have two linear maps $f$ and $g$ represented by matrices $A$ and $B$.
- The matrix for $(f\circ g)(\mathbf{v})=f(g(\mathbf{v}))$ is just $AB$

### Matrix Multiplication


> [!success] Method
> Given matrices $A\in\mathbb{R}^{m\times n}$ and $B\in\mathbb{R}^{m\times k}$, the elements $c_{ij}$ of the product $C=AB\in\mathbb{R}^{m\times k}$ are $$c_{ij}=\sum^{n}_{l=1}a_{il}b_{lj}$$
> For $1\leq i\leq m, 1\leq j\leq k$

- also formalises definition of multiplying matrix by a vector $k=1$.

Example: $$\begin{pmatrix} 1 & 2 & 3 \\ 3 & 2 & 1\end{pmatrix}\begin{pmatrix} 0 & 2 \\ 1 & -1 \\ 0 & 1\end{pmatrix}=\begin{pmatrix} 0 + 2 + 0 & 2 -2 + 3 \\ 0 + 2 + 0 & 6 -2 + 1\end{pmatrix}=\begin{pmatrix} 2 & 3 \\ 2 & 5\end{pmatrix}$$

