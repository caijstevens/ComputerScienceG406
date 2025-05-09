#ads 

### Walks, Paths, Cycles and Distances

> [!info] Definition
> A **walk** in a graph $G$ is a sequence of edges $v_0v_1,v_1v_2,v_2v_3,\dots,v_{n-1}v_n$.
> Can also say that $v_0,v_1,\dots,v_n$ is a walk in $G$.
 
 - walk in $G$ is a **path** if all $v_i$s are distinct, and therefore $v_0,v_1,\dots,v_n$ would be a path in $G$.
 
 >[!info] Definition
 >A walk $v_0,v_1,\dots,v_n$ with $v_0 = v_n$ is a **circuit** or **closed walk**.
 
- a closed walk is a **cycle** (simple circuit) if all other $v_i$s are distinct.

If $G$ is directed graph then **directed paths** and **directed cycles** are defined naturally
- each edge directed from $v_i$ to $v_{i+1}$.

> [!info] Definition
> The **length** of a path/cycle is the number of edges.

> [!info] Definition
> The **distance** between vertices $u$ and $v$ in a graph, $dist(u,v)$, is the shortest path length from $u$ to $v$ if path exists, and $\infty$ otherwise.

> [!info] Definition
> The **diameter** of a graph is largest distance between two vertices.

Example: Acquaintance Graph ("six degrees of separation"):
- graph of diameter 6 where vertices are all people and edge present if two people acquainted.
- "small world phenomenon"

### Connectivity

In a graph, **shortest-path problem** is problem of computing path from one given vertex to another with smallest total length.

> [!info] Definition
> A graph $G=(V,E)$ is **connected** if there exists a path in $G$ between every pair of vertices $u,v$.
> A **connected component** of $G$ is a **maximal** connected subgraph of $G$.

**Connected components theorem**:
> [!info] Theorem
> Every graph $G=(V,E)$ contains at least $|V|-|E|$ connected components.
- **Corollary:** If $G=(V,E)$ is connected then $|E|\geq |V|-1$.
> [!summary] Proof
> By induction over $m=|E|$.
> **Induction basis**: $m=0$. No edges, only isolated vertices. $|V|$ connected components.
> **Induction step:** Let $G=(V,E)$ with $|E|=m+1$. Consider arbitrary $e\in E$, and define $E'=E\setminus\{e\}$.
> By induction hypothesis: $G'=(V,E')$ has at least $|V|-|E'| = |V|-m$ connected components. Two cases:
> 1. With $e$, number of connected components does not change.
> 2. With $e$, number of connected components decreases by 1.
> 
> In both cases, $G$ has at least $|V|-m-1 = |V|-|E|$ connected components.

A directed graph $G$ is called **(weakly) connected** if it is connected after forgetting directions.
- directed graph is **strongly connected** if any two distinct vertices connected by directed paths in both directions.
- a **strongly connected component** of digraph $G$ is maximal strongly connected subgraph of $G$.

> [!info] Definition
> An **Eulerian circuit** is a graph where, starting and finishing at the same vertex, each edge is traversed **exactly once**.

> [!info] Theorem
> A connected graph with $\geq 2$ vertices has Eulerian circuit iff each of its vertices has even degree.
> 

> [!summary] Idea of Proof:
> Necessity ($\Rightarrow$): each time circuit passes through vertex $v$, contributes 2 to $deg(v)$. Each edge used once, so $deg(v)$ must be even.
> Sufficiency ($\Leftarrow$): induction on the number of vertices in G. Induction base: $G=K_3$, claim obvious. Induction step:
> 1. start from any vertex $u$ along untraversed edges, marking off traversed edges.
> 2. stop when arrive at vertex where can't continue. Must be $u$ again.
> 3. hence have circuit $C$. Delete from $G$ to obtain smaller graph $H$ in which all degrees also even.
> 4. by induction hypothesis, each connected component of $H$ has Eulerian circuit.
> 5. combine $C$ and these circuits to obtain required circuit for $G$.



> [!info] Definition
> A **Hamiltonian cycle** is a graph where, starting and finishing at the same vertex, each vertex is visited **exactly once**.
- detecting Hamiltonian cycles is hard (NP-complete).

### Travelling Salesman Problem (TSP)

**Premise**: Salesman should visit cities $c_1,c_2,\dots,c_n$ in some order, visiting each once and returning to start.
- postive int **cost** $d(i,j)$ **of travel** between each pair $(c_i,c_j)$ is known.
- **goal**: find optimal (cheapest) route

Given graph $G$ with set $V$ of vertices $(|V|=n)$ and set $E$ of edges:
- for each vertex $v$ create a city $c_v$.
- for each pair of distinct $u,v\in V$, set $d(c_u,c_v)=1$ if $uv\in E$ and $d(c_u,c_v) = 2$ otherwise.

Then detecting Hamiltonian cycle in $G$ can be viewed as TSP.
- if $G$ has Hamiltonian cycle then cycle is route of cost exactly $n$.
