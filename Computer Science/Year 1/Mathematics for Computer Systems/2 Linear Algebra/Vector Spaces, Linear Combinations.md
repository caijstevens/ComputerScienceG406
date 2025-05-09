#mcs 

### Vector Space

A **vector space** is a mathematical structure as it has sets, operations and axioms.
- has two sets: scalars $F$ and vectors $V$.
- $V$ forms commutative group under addition $\mathbf{u} + \mathbf{v} = \mathbf{v}+\mathbf{u}$
- $F$ forms a field.
- Scalar multiplication: $F\times V\rightarrow V$


> [!summary] Notation Conventions
> 1. Write vector variables in bold $\mathbf{u},\mathbf{v}\in V$
> 2. Alternatives are $\overline{v}, \underline{v}, \vec{v}$
> 3. Write scalars plain $a,b\in F$
> 4. Vectors in $R^3$ as row $(1,-2,0)$ or column $$\begin{pmatrix} 1 \\ -2 \\ 0 \end{pmatrix}$$

> [!success] Vector Space Axioms
> 1. (commutative group and field axioms for vectors and scalars)
> 2. $a(b\mathbf{v}) = (ab)\mathbf{v}$
> 3. $1\mathbf{v}=\mathbf{v}$
> 4. $a(\mathbf{u}+\mathbf{v}) = a\mathbf{u}+a\mathbf{v}$
> 5. $(a+b)\mathbf{v}=a\mathbf{v}+b\mathbf{v}$

Examples of vector spaces:
- $\mathbb{R}^3=\mathbb{R}\times\mathbb{R}\times\mathbb{R}$ over $\mathbb{R}$
	- vectors in $\mathbb{R}^3$, scalars in $\mathbb{R}$
- $\mathbb{Z}^8_2 \space$ (equivalent to $(\mathbb{Z}_2)^8$) over $\mathbb{Z}_2$
- polynomials over $\mathbb{R}$

### Linear Combinations

> [!info] Definition
> Given vectors $\mathbf{v_1},\dots,\mathbf{v_n}$ and scalars $a_1,\dots,a_n$, we can form a **linear combination**: $$a_1\mathbf{v_1}+\dots+a_n\mathbf{v_n}$$ 
> Alternatively $$\sum^{n}_{i=1}a_i\mathbf{v_i}$$

### Span and Spanning Sets

> [!info] Definition
> The **span** of a set of vectors is the set of all linear combinations in the set.
- if the field is infinite then the span will be infinite

Example:
- Given the set $\{(0,1,0),(0,1,2)\}$
- The **span** of this set is all **linear combinations** of the vectors $\alpha(0,1,0)+\beta(0,1,2)$ for scalars $\alpha,\beta$ (can be any value). Therefore the span is:$$\alpha(0,1,0)+\beta(0,1,2)=(0,\alpha+\beta,2\beta)$$
- The set represents the plane spanned by the $y$-vector $(0,1,0)$ and the $y$-$z$-vector $(0,1,2)$. It sits in the $x=0$ slice (the $yz$-plane) as $x$ is $0$ in both vectors in the set.

> [!info] Definition
> A set of vectors $S$ is a **spanning set** for a vector space $(F,V)$ if $span(S)=V$.

Example:
- The set $\{(1,0),(0,1)\}$ spans $\mathbb{R}^2$ 
- Because any vector $(x,y)$ in $\mathbb{R}^2$ can be written as: $$x(1,0)+y(0,1)=(x,y)$$
- Equivalently, $\{(1,0,0),(0,1,0),(0,0,1)\}$ spans $\mathbb{R}^3$
- Because any vector $(x,y,z)$ can be written as:$$x(1,0,0)+y(0,1,0)+z(0,0,1)=(x,y,z)$$
### Linear (In)dependence

> [!info] Definition
> A set of vectors $S=\{\mathbf{s_1},\dots,\mathbf{s_n}\}$ is **linearly dependent** if there exists a linear combination: $$\sum^{n}_{i=1}a_i\mathbf{s_i}=0 \text{ and }\exists i.a_i\neq 0$$
- means we can write (at least) one of them as a linear combination of the others
- this basically says that vectors are linearly dependent if there is a non-zero linear combination of them that equals 0.
- a set of vectors is **linearly independent** if the above is not possible.

### Basis of a Vector Space

> [!info] Definition
> A subset $S$ of a vector space $V$ is a **basis** for $V$ if $S$ spans $V$ **and** $S$ is linearly independent. In other words, $S$ is the minimal spanning set we can find for $V$.

- the standard basis for $\mathbb{R}^3$ is $\{(1,0,0),(0,1,0),(0,0,1)\}$.
	- sometimes written $\{\hat{\mathbf{i}},\hat{\mathbf{j}},\hat{\mathbf{k}}\}$

### Dimension of a Vector Space

> [!info] Definition
> The **dimension** of a vector space is the cardinality (size) of its basis.
- the dimension of $\mathbb{R}^3$ is 3.
- all basis sets for a vector space are the same size.
- dimension can be infinite, e.g. the space $\mathbb{R}[x]$ (the set of all polynomials with real coefficients).
	- set $\{1,x,x^2,x^3,...\}$ is linearly independent and spans $\mathbb{R}[x]$, therefore is its basis. This set is infinite, therefore the space has infinite dimension.
