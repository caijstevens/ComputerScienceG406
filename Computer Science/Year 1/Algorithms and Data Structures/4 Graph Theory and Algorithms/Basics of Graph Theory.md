#ads 

### Graphs

**Graphs** are representations of objects and relations between them
- relations between pairs of objects


> [!info] Definition
> A graph $G$ is a pair $(V(G), E(G))$, where $V(G)$ is a **nonempty** set of **vertices** (nodes) and $E(G)$ is a set of **unordered pairs** $\{u,v\}$ with $u, v \in V(G)$ and $u\neq v$, called the **edges** of G
- $V(G)$ can be infinite
- often write $uv$ instead of $\{u,v\}$
- if graph $G$ is clear from context, write $V$ and $E$ instead of $V(G)$ and $E(G)$
![[Screenshot 2025-04-26 at 21.26.40.png]]

### Terminology

Let $G$ be a graph and $uv$ an edge in it:
- $u$ and $v$ are **endpoints** of edge $uv$
- $u$ and $v$ are **neighbours** or **adjacent** vertices
- $uv$ is **incident** to $u$ and to $v$
- if $vw$ also an edge (where $w \neq u$) then $uv$ and $vw$ are **adjacent**

Let $G = (V,E)$ be a graph. 
- the **neighbourhood** of a vertex $v \in V, N(v)$ is the set of neighbours of $v: N(v) = \{u\in V | \space uv \in E \}$.
- the **degree** of a vertex $v \in V, \space deg(v)$ is the number of neighbours of $v$, so $deg(v)=|N(v)|$.
- $\delta$ or $\delta(G)$ denotes the **smallest degree** in $G$, and $\Delta$ or $\Delta(G)$ denotes the **largest degree**
- vertex of degree 0 is an **isolated vertex**
- vertex with degree 1 is an **end vertex** or **pendant vertex**

A **subgraph** $G' = (V', E')$ of $G=(V,E)$ is a graph with $V' \subseteq V$ and $E' \subseteq E$.
- subgraph is **proper** if $G' \neq G$ and **spanning** if $V' = V$.
- it is an **induced subgraph** if $E'$ contains all edges of $E$ between vertices of $V'$ (obtained by removing all vertices and edges of $V \setminus V'$)

### Types of Graphs

**Directed** graphs or **digraphs**: edges can have **directions**

> [!info] Definition
> A **directed graph** $G$ is a pair $(V(G), E(G))$, where $V(G)$ is a **nonempty** set of **vertices** (nodes) and $E(G)$ is a set of **ordered pairs** $\{u,v\}$ with $u, v \in V(G)$ and $u\neq v$, called the **edges** of G
- e.g. the Web graph: vertices are webpages, edges are hyperlinks

**Multi-graphs**: multiple edges are allowed between two vertices
- e.g. airlink graph: several different airlines can fly between two towns

**Pseudo-graphs**: edges of the form $uu$ (loops) are allowed
- e.g. region pseudo-graph in graphics: vertices are connected regions, edges mean "can get from one to other by crossing fence"

**Vertex- or edge-weighted graphs**: vertices/edges can have weights
- e.g. road map graph: weights on edges are distances

By default, all graphs are **simple undirected** or **simple directed** (sometimes edge-weighted too)\ so no multiple edges or loops

### Types of Subsets

**Independent set**: set of vertices which are not connected to each other

**Maximum independent set**: largest independent set within a graph

**Minimum colouring**: partition into the smallest number of independent sets

**Dominating set**: for a directed graph, the dominating set is the set of vertices that collectively have an edge directed towards every other vertex

**(Minimum) Dominating set**: smallest dominating set within a graph

### Examples of Graph Models

Graphs can express **conflicting** situations between objects
- e.g. vertices: base stations for mobile phones, edges: overlapping service areas
- e.g. vertices: traffic flows at a junction, edges: conflicting flows

Graphs can be used for **analysing strategies and solutions**
- e.g. vertices: states in a game, edges: transitions between states
- e.g. vertices: steps in solution, edges: transitions between steps

### First Theorem in Graph Theory


> [!info] Theorem (Handshaking Lemma)
> Let $G=(V,E)$ be a graph. Then $\sum_{v\in V} deg(v) = 2|E|$.

> [!summary] Proof
> Every edge has two endpoints and contributes one to each of their degrees, so contributes two to the sum of the degrees of all the vertices of V

In every undirected graph $G$, the number of vertices with an odd degree is even.

> [!summary] Proof
> Let $G = (V,E)$. Partition $V$ to two subsets:
> 		- $V_{odd} = \{v:deg(v)\space \text{is odd}\}$
> 		- $V_{even} = \{v:deg(v)\space \text{is even}\}$
> Clearly, $\sum_{v\in V_{even}} deg(v)$ is even. By the Handshaking Lemma it follows that:
> 
> $$\sum_{v\in V_{odd}} deg(v) = 2\cdot |E| - \sum_{v\in V_{even}} deg(v)$$
> is even too.
> - If we have an odd number of vertices with odd degree, then $\sum_{v\in V_{odd}} deg(v)$ is odd, a contradiction.
> - Therefore must be an even number of vertices with odd degree.

### Most Basic Graph Classes

Some graphs appear so often that they have dedicated names/symbols.
- in general we define $P_n$ as the path on $n$ vertices
- graph with vertex set $V = \{v_1, v_2, \dots, v_n\}$ and edge set $E = \{v_1v_2, v_2v_3, \dots, v_{n-1}v_n\}$.
- therefore $P_n$ has $n-1$ edges


> [!info] Definition
> A **path** in a graph $G$ is a subgraph of $G$ which is isomorphic to the graph $P_k$ for some integer $k\geq 1$. Can be called a **simple path**.

In general a $C_n$ on $n$ vertices is defined similarly to the $P_n$ but with an additional edge between $v_n$ and $v_1$.
- therefore $C_n$ has $n$ edges.

> [!info] Definition
> A **cycle** in a graph $G$ is a subgraph of $G$ which is isomorphic to the graph $C_k$ for some integer $k\geq 3$. Can be called a **simple circuit**.

In general a $K_{p,q}$ graph consists of two disjoint vertex sets on $p$ and on $q$ vertices and all possible edges between these two vertex sets.
- therefore $K_{p,q}$ has $p\cdot q$ edges.

> [!info] Definition
> $K_{p,q}$ is called a **complete bipartite** graph. Any subgraph of $K_{p,q}$ is a **bipartite** graph.
> A graph is bipartite if and only if vertex set can be partitioned to two vertex sets such that every edge has one endpoint in each set.
- bipartite graphs often used in scheduling and assignment problems.

### More Graph Classes

> [!info] Definition
> A **complete** graph on $n$ vertices, $K_n$, contains all possible edges between pairs of vertices.
- $K_n$ has $\frac{1}{2}n(n-1)$ edges.


> [!info] Definition
> The (**n-dimensional**) **hypercube** or **n-cube** $Q_n (n\geq 1)$ is graph with $$V = \{(e_1,\dots,e_n)|e_i \in \{0,1\} (i=1,\dots,n)\}$$ in which two vertices are neighbours if and only iff the corresponding rows differ in exactly one entry.

---

> [!info] Theorem
> All n-cubes are bipartite.

> [!summary] Proof
> We give a **bipartition** of the vertex set of the n-cube
> Let $V_1$ contain all the vertices with **odd** number of 1s
> Let $V_2$ contain all vertices with **even** (maybe 0) number of 1s
> This is clear partition of $V$ into two disjoint sets
> Each edge has one endpoint in each set
> Therefore all n-cubes are bipartite
