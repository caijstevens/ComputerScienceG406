 #mcs 

### Pythagoras' Theorem

> [!info] Theorem
> $c^2=a^2+b^2$

### Area of Unit Square Image

Linear map $f:\mathbb{R}^2\rightarrow\mathbb{R}^2$ is represented by $$\begin{pmatrix} a & b \\ c & d\end{pmatrix}$$

> [!summary] Example
> Find the area covered by the quadrilateral whose corners are $$f((0,0)), f((1,0)), f((1,1)), f((0,1))$$
> 
> The area of any shape after applying $f$ is $$\text{Area after }f=|\det(A)| \times (\text{Area before } f)$$
> Unit square has area 1, so the area after the transformation is: $$|\det(A)| \times 1=|\det(A)|$$
> 

### Determinant of a 2x2 Matrix

Determinant of matrix $A$ is written as $\det(A)$ or $|A|$.

> [!todo] Formula
> For a 2x2 matrix: $$det(\begin{pmatrix} a & b \\ c & d\end{pmatrix})=\begin{vmatrix} a & b \\ c & d\end{vmatrix} = ad-bc$$
> 
> 
- the determinant is the signed area of the image of the unit square.


> [!summary] Example
> $$\begin{vmatrix} 1 & -2 \\ 3 & -4\end{vmatrix} = 1\cdot(-4)-(-2)\cdot 3=2$$
- determinant = 0 means that columns are **linearly dependent**.
- only **square** matrices have a determinant

### Determinant of nxn matrix

If a matrix $A$ is made out of columns vectors $\mathbf{c}_1,\dots,\mathbf{c}_n$, we can define the function on the columns: $$\det(A) = \det(\mathbf{c}_1,\dots,\mathbf{c}_n)$$
det() Definitions:
1. **Linearity**: linearity in each column so that $$\det(a\mathbf{c}_1,\dots,\mathbf{c}_n) = a\cdot\det(\mathbf{c}_1,\dots,\mathbf{c}_n)$$ $$\det(\mathbf{c}_1,\dots,a\mathbf{c}_n) = a\cdot\det(\mathbf{c}_1,\dots,\mathbf{c}_n)$$ $$\det(\mathbf{c}_1 + \mathbf{c}_1,\dots,\mathbf{c}_n) =\det(\mathbf{c}_1,\dots,\mathbf{c}_n) + \det(\mathbf{c}_1,\dots,\mathbf{c}_n)$$
2. **Alternating**: If $\mathbf{c}_i=\mathbf{c}_j$ for some $i\neq j$ then $\det(A)=0$.
3. **Identity**: The determinant of the identity matrix $I_n$ is $1$.

### Area/Volume based Rationale

> [!summary] Rules
> 1. Doubling one of the vectors doubles the area/volume.
> 2. We can add together the area/volumes of rectangles/cuboids/hypercuboids.
> 3. If the image of two vectors is the same then the image space has collapsed e.g. from 3D to 2D.
> 4. The unit square/cuboid/hypercuboid has area/volume 1.

### Properties of Determinants

> [!summary] Properties
> 1. If a matrix $B$ is like $A$ but with two columns swapped then $\det(B)=-\det(A)$
> 2. Consider $\det(\mathbf{c}_1 + \mathbf{c}_2, \mathbf{c}_1 + \mathbf{c}_2, \mathbf{c}_3,\dots, \mathbf{c}_n)$
> 3. Remember repeated columns have determinant $0$.
> 4. If a matrix $A$ has a column made up of zeros then $\det(A)=0$
> 5. If a scalar multiple of one column is added to another column, the determinant is unchanged.
> 6. If a matrix $A$ has columns that are linearly dependent then $\det(A)=0$.

### Determinant of Diagonal Matrix

> [!warning] Helpful Note
> The determinant of a diagonal matrix can be found by simply multiplying the values on the diagonal together. $$\det(D) = \prod^{n}_{i=1}d_i$$

> [!summary] Example
> $$\begin{vmatrix} 2 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & -3\end{vmatrix} = 2 \cdot \begin{vmatrix} 1 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & -3\end{vmatrix}$$
> $$= 2\cdot 4\cdot\begin{vmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -3\end{vmatrix}$$
> $$=2\cdot 4\cdot -3\cdot\begin{vmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1\end{vmatrix}$$
> $$=-24$$
> 

### Determinant of 3x3


> [!todo] Method and Formula
> 1. Expand out first column: three terms
> 2. Expand out second column: each one has two non-zero terms
> 3. Expand out third column: each one has one non-zero term
>    
> For a given matrix: $$A = \begin{vmatrix} a & b & c \\ d & e & f \\ g & h & i\end{vmatrix}$$
> The determinant is $\det(A)=a(ei-fh)-b(di-fg)+c(dh-eg)$

### Determinant of nxn

> [!todo] Laplace Expansion Formula
> $$\det(C)=\sum^{n}_{j=1}(-1)^{i+j}c_{ij}M_{ij}$$
> Where $M_{ij}$ is the minor: the determinant of the matrix $C$ with row $i$ and column $j$ removed.

### Combining Matrices

> [!todo] Formula
> $$\det(AB) =\det(A)\cdot\det(B)$$
> $$\det(A^{-1})=\frac{1}{\det(A)}$$
### Uses of Determinants

> [!success] Examples
> 1. Finding area\volume of images
> 2. Asserting linear (in)dependence
> 3. Asserting if matrix has an inverse (if $\det(A)\neq 0$)
> 4. Finding inverse of a matrix
> 5. Solving equations with matrices


