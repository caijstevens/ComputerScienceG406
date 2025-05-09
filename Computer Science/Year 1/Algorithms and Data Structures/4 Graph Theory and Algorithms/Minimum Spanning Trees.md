#ads 

### Minimum Spanning Tree Problem

**Problem:** Find **tree** that **spans** the vertices and has **minimum** cost.
- has $|V|-1$ edges
- has no cycles
- might not be unique

### Representations of Weighted Graphs

Use adjacency matrices:![[Screenshot 2025-04-28 at 11.51.17.png]]

> [!danger] Warning
> Be careful: an entry $A(i,j)=0$ means "the edge $(v_i,v_j)$ does not exist". This is not the same as "edge $(v_i,v_j)$ has weight 0".
- as we are looking for a **minimum cost** spanning tree, can think of "$A(i,j)=0$" as "$w(i,j)=\infty$".
![[Screenshot 2025-04-28 at 11.53.38.png]]

### Kruskal's Algorithm

> [!todo] Algorithm Process
> 1. Sort edges by weight.
> 2. Let $A=\varnothing$.
> 3. Consider edges in increasing weight order. For each edge $e$, add $e$ to $A$ unless would create cycle.
- **running time is** $O(E\log V)$.

### Prim's Algorithm

> [!todo] Algorithm Process
> 1. Let $U = \{u\}$ where $u$ is arbitrarily chosen vertex.
> 2. Let $A=\varnothing$.
> 3. Until $U$ contains all vertices: find least-weight edge $e$ that joins vertex $v$ in $U$ to vertex $w$ not in $U$ and add $e$ to $A$ and $w$ to $U$.
- **running time is** $O(V\log V + E)$.

### Generic MST Algorithm

Both Kruskal and Prim are special cases of generic greedy MST-algorithm.
- iteratively build vertex set $A$ such that **$A$ is subset of some MST.**


> [!info] Definitions
> 1. Let $A$ be subset of MST. If set $A \cup \{(u,v)\}$ is also subset of an MST, $(u,v)$ is a **safe** edge for $A$.
> 2. A **cut** $(S,V-S)$ of $G=(V,E)$ is a partition of $V$.
> 3. An edge $(u,v) \in E$ **crosses** the cut $(S,V-S)$ if $u\in S$ and $v\in V-S$ (or vice versa).
> 4. An edge $(u,v)\in E$ is a **light edge** crossing a cut if weight is smallest among all edges crossing cut.
> 5. A cut **respects** a set $A$ of edges if no edge of $A$ crosses the cut.

```GENERIC-MST(G,w)
def GENERIC-MST(G,w):
	A = Null
	while A does not form a spanning tree
		do find an edge (u,v) that is safe for A
		A = A union {(u,v)}
	return A
```

> [!info] Theorem
> Let $G=(V,E)$ be connected undirected graph with real-values weight function $w$ defined on edges $E$. Let $A\subseteq E$ such that $A$ is included in some MST of $G$, let $(S,V-S)$ be any cut of $G$ such that respects $A$, and let $(u,v)$ be a light edge crossing $(S,V-S)$. Then the edge $(u,v)$ is **safe** for $A$.
- implies correctness for Prim's algorithm.

> [!success] Corollary
> Let $G=(V,E)$ be connected undirected graph with real-values weight function $w$ defined on edges $E$. Let $A\subseteq E$ such that $A$ is included in some MST of $G$, and let $C = (V_C, E_C)$ be a connected component (tree) in the forest $G_A = (V,A)$. If $(u,v)$ is a light edge that connects $C$ to some other component in $G_A$, then the edge $(u,v)$ is **safe** for $A$.
> 

> [!summary] Proof
> The cut $(V_C,V-V_C)$ respects $A$, and $(u,v)$ is a light edge for this cut. Therefore $(u,v)$ is safe for $A$ by the above theorem.
- this corollary implies correctness for Kruskal's algorithm.
