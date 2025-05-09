#mcs 

### Abstraction

**Abstraction** allows generalisation
- can build structures using other structures
- multiple layers of abstraction, e.g. assembly instruction, VM instruction etc.
- algebra is a form of abstraction


> [!info] Definition
> A **mathematical structure** typically defines sets, operations and axioms.
> 
> **Axioms** are the rules which define a mathematical structure.

- operations are related to each other and are also abstract.

### Groups

**Groups** have a **set** $G$, a **binary operation** $\star$ and some **axioms**.

> [!success] Group Axioms
> 
> 1. $\star$ is **closed** on $G$ i.e. $\star : G\times G\rightarrow G$
> 2. $\star$ is **associative** i.e. for all $a,b,c$ in $G$, $a\star(b\star c)=(a\star b)\star c$
> 3. There exists an **identity element** $e \in G$ i.e. $\forall a\in G . a\star e=e\star a=a$
> 4. $\star$ has an **inverse operator** i.e. $\forall a\in G . \exists b\in G . a\star b=b\star a=e$
- $\star$ is an abstract operation, like $f$ and $x$ are often abstract functions\values

Examples of groups:

| Set                               | Binary operation |
| --------------------------------- | ---------------- |
| $\mathbb{R}$                      | $+$              |
| $\mathbb{Z}$                      | $+$              |
| symmetries                        |                  |
| even numbers                      | $+$              |
| set of $\mathbb{Q} \setminus {0}$ | multiplication   |
- the symmetry group of a geometric object is the group of all transformations under which the object is **invariant**.

In general, can study $\mathbb{Z}_n$ modulo arithmetic.
- $\mathbb{Z}_n$ is the set of integers modulo $n$.
- For example, $\mathbb{Z}_4 = \{0,1,2,3\}$
- operation is addition modulo 4 e.g. $a+b \mod{4}$

Can use Cayley tables to write out full operation table for $\mathbb{Z}_4$:
![[Screenshot 2025-05-05 at 23.16.36.png]]

### Fields

> [!info] Definition
> A **field** is a set $F$ together with **two** binary operations on $F$, addition and multiplication, which are mappings on $F$ of $F\times F\rightarrow F$.
- parts of a field are groups, but a field itself is more than just a group.
- not every group can be turned into a field.

Finite fields can exist.
- a finite field exists iff its size is a prime power. $$|F| = p^n \space\text{where}\space p\space\text{is a prime, and}\space n\in\mathbb{N}$$

> [!success] Field Axioms
> 1. **Closure**: For all $a,b\in F, a+b\in F$. Also, for all $a,b\neq 0, a\cdot b\neq 0$ and $a\cdot b\in F$.
> 2. **Associativity**: $(a+b)+c=a+(b+c)$. Also, $(a\cdot b)\cdot c=a\cdot (b\cdot c)$.
> 3. **Identity**: There is an element $0$ (zero) in $F$ such that $a+0=a$. Also, there is an element $1$ (one) in $F$ such that $a\cdot 1=a$.
> 4. **Inverses**: For every $a\in F, \exists(-a)\in F . a + (-a)=0$. Also, for every $a\neq 0, \exists a^{-1} . a\cdot a^{-1}=1$.
> 5. **Commutativity**: $a+b=b+a$, and $a\cdot b=b\cdot a$.
> 6. **Distributivity**: $a\cdot(b+c)=a\cdot b+a\cdot c$ for all $a,b,c\in F$.

### Structures with Multiple Sets

> [!info] Definition
> A **vector** is a quantity having direction as well as magnitude, especially as determining the position of one point in space relative to another.

- vectors can be added
- vectors can be scaled (multiplied by a scalar)
- scalars can be added
- there is no general multiplication of two vectors but the following alternatives are available:
	- scalar multiplication, $\lambda \vec{v}$
	- dot product, $\vec{u}\cdot \vec{v} = u_1v_1 + u_2v_2 + \cdots + u_nv_n$
	- cross product (only in $\mathbb{R}^3$), $\vec{u} \times \vec{v}$


