#ads 

### Trees


> [!info] Definition
> A **forest** is an **acylic** graph (has no cycles)
> A **tree** is a **connected forest** e.g. connected acyclic graph.

![[Screenshot 2025-04-27 at 14.34.18.png]]

### Spanning Trees

A subgraph $G' = (V',E')$ of a graph $G=(V,E)$ is **spanning** if $V'=V$.

> [!info] Theorem
> Every connected graph contains a spanning tree (a spanning subgraph that is a tree).

> [!summary] Proof
> Let $G$ be a connected graph.
> If $G$ contains no cycles, is tree, therefore spanning tree of itself.
> If $G$ contains cycle, can remove one edge from cycle.
> New graph still connected.
> By repeating, can destroy all cycles, end up with spanning tree.

- finding **min-weight spanning trees** in edge-weighted graphs is important task.

### Leaves in Trees

**Leaf** in a tree is vertex of degree 1.

> [!info] Lemma
> Every tree on at least two vertices contains a leaf.

> [!summary] Proof
> By **contradiction**:
> Assuming that every vertex has degree 0 or at least 2, show that graph is not a tree.
> If vertex has degree 0, then the graph is not connected, therefore not tree.
> If every vertex has degree at least 2, we will always encounter a vertex we have already visited.
> Implies that graph contains a cycle, therefore not a tree, therefore contradiction.

> [!summary] Alternative Proof
> (When every vertex has degree at least 2):
> Consider longest path $P$ and end vertex $v$ of $P$.
> All neighbours of $v$ are on $P$.
> If $deg(v)\geq 2$, there is a cycle.
> Same holds for other end vertex $u$ of $P$.
> $deg(u) = deg(v) = 1$.

### Edges of Trees

> [!info] Theorem
> A connected graph on $n$ vertices is a tree iff it has $n-1$ edges.

> [!summary] Proof
> $(\Rightarrow)$. Show by **induction** on $n$, that a tree on $n$ vertices has $n-1$ edges.
> For small $n$ lemma holds, tree on one vertex has no edges, tree on two vertices has one edge.
> **Induction hypothesis**: Suppose each tree on $n-1$ vertices has $n-2$ edges
> Take a tree $T$ on $n$ vertices for some $n\geq 3$.
> $T$ contains leaf $v$. Consider graph $T-v$, has one vertex less and one edge less than $T$.
> $T-v$ still connected and acyclic.
> $T-v$ has $n-1$ vertices and $n-2$ edges.
> $T$ has one edge more, so $n-1$ edges.
> 
> $(\Leftarrow)$.
> Assume that $G$ is connected graph with $n$ vertices and $n-1$ edges.
> Then, as before, $G$ contains spanning tree $T$.
> As before, $T$ contains exactly $n-1$ edges.
> $T$ is subgraph of $G$, same number of edges as $G$.
> Hence, $T$ and $G$ are same.
> Therefore $G$ is a tree.


### Paths in Trees


> [!info] Lemma
> Let $T$ be a tree and $u,v\in V(T)$ with $u\neq v$.
> Then there is a **unique path** in $T$ between $u$ and $v$.

> [!summary] Proof
> By **contradiction**.
> There is a path between $u$ and $v$ in $T$, since $T$ is connected.
> Suppose there are two paths $P$ and $Q$ in $T$ between $u$ and $v$ and derive contradiction.
> Let $x$ and $y$ in $V(T)$ be distinct, chosen in way that $x$ and $y$ on both $P$ and $Q$, but between $x$ and $y$ vertices on $P$ and $Q$ are disjoint.
> Segments of $P$ and $Q$ between $x$ and $y$ together form cycle.
> **Contradicts** that $T$ is tree. Therefore there is a unique $(u,v)$-path in $T$.

 ### Rooted Trees, Children and Parents

> [!info] Definition
> A **rooted tree** is a tree in which one vertex is fixed as the **root**.
- draw in horizontal levels starting with root at level 0, work downwards.

Let $v$ be a vertex in a rooted tree $T$.
- neighbours of $v$ in the next level are **children** of $v$.
- unique neighbour of $v$ in previous level (if $v$ not root) is the **parent** of $v$.
- if $v$ has no children it is a **leaf** of $T$.
- if $v$ has children, then it is an **internal** vertex.

Some applications of trees:
- binary search trees
- search trees
- phylogenetic trees (bioinformatics)

### Number of Leaves in Trees

> [!info] Lemma
> A tree with at least 2 vertices, $n_3$ of which have degree at least 3, has at least $n_3 +2$ leaves.

> [!summary] Proof
> Let $T$ be a tree on $n\geq 2$ vertices. Use induction on $n$.
> Let $\ell(T)$ denote number of leaves in $T$, and $n_3(T)$ denote number of vertices of degree at least 3 in $T$.
> **Induction base**: if $n=2$, then $n_3=0$ and $T$ has 2 leaves.
> **Step**: Now suppose that every tree on $< n$ vertices has at least $n_3 + 2$ leaves, consider tree $T$ on $n\geq 3$ vertices.
> Since $T$ is tree on at least 3 vertices, $T$ has leaf $u$.
> Then $T'=T-u$ is tree on $n-1$ vertices. By induction hypothesis, we have $\ell(T') \geq n_3(T') + 2$.
> Let $v$ be the unique neighbour of $u$ in $T$.
> $T$ is connected and has at least 3 vertices, so $v$ has at least 2 neighbours in $T$.
> Rest by **case analysis**:
> ![[Screenshot 2025-04-27 at 15.24.02.png]]

### Trees and Bipartite Graphs

> [!info] Theorem
> Every tree is a bipartite graph.

> [!summary] Proof
> Give **direct** proof. Use known result on unique paths in tree $T$ to define bipartition of vertex set $V(T)$.
> Choose a vertex $v$ and put vertex in set $V_1$.
> For every vertex $u\neq v$, unique path from $v$ to $u$ in $T$, consider path length.
> If length odd, put $u$ in $V_2$; otherwise $V_1$.
> We have to show that this is a valid bipartition.
> $V_1$ and $V_2$ are disjoint and together make up $V(T)$.
> Every edge has end vertices in both $V_1$ and $V_2$.
> Completes proof.

### Graph Isomorphism


> [!info] Definition
> Two graphs $G=(V,E)$ and $G'=(V',E')$ are **isomorphic** if exists a **bijective** function $f:V\rightarrow V'$ such that for every $u,v \in V$ we have $uv\in E$ iff $f(u)f(v)\in E'$. Then write $G\cong G'$.

In other words, $G \cong G'$ when:
- exists correspondence between vertices of $G$ and $G'$ which maintains neighbourhood property.
- there is renaming of $G'$ such that it coincides with $G$.

Isomorphism is equivalence relationship.
- $G \cong G$ means that every graph is isomorphic to itself.
- if $G_1\cong G_2$ and $G_2\cong G_3$, then $G_1\cong G_3$.

Deciding whether $G$ and $G'$ are isomorphic is neither an easy (poly-time) problem nor a hard (NP-complete) problem.
- if they are isomorphic, they share **all** structural characteristics:
	- number of vertices and edges
	- degree sequence
	- strength of connectivity
	- eulerian\hamiltonian circuit
	- chromatic number
	- size of largest independent set
- none of the above alone can determine isomorphism
	- can only be used to show **non-isomorphism**

### Graph Isomorphism on Rooted Trees

**Undirected** rooted trees can exist.
- a tree $T$ and a specially designated vertex $r$ (root)\.

> [!info] Definition
> Two **rooted** trees $T_1(V_1,E_1,r_1)$ and $T_2(V_2,E_2,r_2)$ are called **isomorphic** if exists **isomorphism bijection** $f: V_1 \mapsto V_2$ such that $f(r_1) = r_2$.
> 
> In a rooted tree $T$ with root $r$ the **level** $L(i)$ is the set of vertices at distance $i$ from the root $r$.

Isomorphism algorithm for rooted trees:
```LABELVERTEX(T,v)

def LabelVertex(T,v):
	if v is leaf of T then
		label(v) = 10
	else
		for every child w of v do
			l(w) = LabelVertex(T,w)
		Sort the labels of children of v decreasingly: l(w1) >= l(w2) >= ... >= l(wk)
		label(v) = "1"l(w1)l(w2)...l(wk)"0"
	return label(v)
```
```LABELEDTREEISOMORPHISM((T1,r1),(T2,r2))

def LabeledTreeIsomorphism((T1,r1),(T2,r2)):
	label(r1) = LabelVertex(T1,r1)
	label(r2) = LabelVertex(T2,r2)
	if label(r1) = label(r2) then
		return YES
	else
		return NO
```


