#ads 

### Graph Representations

**Adjacency list**:
- for each vertex $v$ list all of the adjacent vertices

**Adjacency matrix**:
- create square matrix $A$
- label rows and columns with vertices
- entry in row $i$ column $j$ is 1 if vertex $j$ adjacent to vertex $i$, 0 if not![[Screenshot 2025-04-28 at 10.50.30.png]]

| representation | space required | init time | copy time | edge insert time | listing time | search edge time |
| -------------- | -------------- | --------- | --------- | ---------------- | ------------ | ---------------- |
| edge array     | $m$            | 1         | $m$       | 1                | $m$          | $m$              |
| adj matrix     | $n^2$          | $n^2$     | $n^2$     | 1                | $n$          | 1                |
| adj list       | $n + m$        | $n$       | $m$       | 1                | $n$          | $deg(u)=O(n)$    |

### Breadth-First Search

BFS maintains **queue** that contains discovered but unprocessed vertices
- BFS colours vertices:
	- white if undiscovered
	- grey if discovered but unprocessed
	- black if processed
- algorithm maintains array $d$ (distance)
	- $d[s] =0$ where $s$ is source vertex
	- if discover new vertex $v$ while processing $u$, set $d[v] = d[u] + 1$

```BFS(G,s)

def BFS(G,s):
	for each vertex u in V[G] - {s} do
		colour[u] = White
		d[u] = infinity
		pi[u] = Nil
	colours[s] = Grey
	d[s] = 0
	pi[s] = Nil
	Q = Null
	Enqueue(Q,s)
	while Q != Null do
		u = Dequeue(Q)
		for each v in Adj[u] do
			if colour[v] = White then
				colour[v] = Grey
				d[v] = d[u] + 1
				pi[v] = u
				Enqueue(Q,v)
		colour[u] = Black	
```

Analysis of running time:
- want **upper bound** on **worst-case** running time.
- assume constant time for each oepration
- initialisation takes time $O(V)$.
- queuing operations take $O(V)$.
- in the **loop**, adj lists of each vertex scanned. each list read once, combined lengths of lists is $O(E)$.
- **total running time**: $O(V +E)$.

Algorithm runs on both directed and undirected graphs
- highlighted edges to discover new vertices form tree: **breadth-first tree**.
- path from $s$ to other vertex $v$ through tree is **shortest path** between $s$ and $v$.
- vertex **predecessor** is one from which it was discovered. can record predecessors in array $\Pi$ when run algorithm, and use array to construct breadth-first tree.

### Depth-First Search

**Depth-first search** explores graph but does not find distances to source
- when vertex discovered, immediately explored
- **timestamps** recorded for **discovery** $d$ and **finish** $f$
- can also record predecessors again
- again, colours used:
	- white for undiscovered
	- grey for discovered but not finished
	- black for finished

```DFS(G)
def DFS(G):
	for each vertex u in V[G]:
		do colour[u] = White
		pi[u] = Nil
	time = 0
	for each vertex u in V[G]:
		do if colour[u] = White
			then DFS-VISIT (u)	
```
```DFS-VISIT(u)
def DFS-VISIT(u):
	colour[u] = Grey
	time = time + 1
	d[u] = time
	for each vertex v in Adj[u]:
		do if colour[v] = White
			then pi[v] = u
			DFS-VISIT(v)
	colour[u] = Black
	f[u] = time = time + 1
```

Analysis:
- initialisation takes time $O(V)$.
- time $O(V)$ spent on incrementing time, colouring vertices and updating $d$ and $f$.
- each vertex in each adj list considered at most once. takes time $O(E)$.
- **total time:** $O(V+E)$.

Edges used for discovering new vertices form **depth-first tree**. can be found with **predecessor array**.
- construct predecessor subgraph after running DFS
- same vertex set, for each vertex $v$ there is edge from predecessor of $v$ to $v$.
- predecessor subgraph is **depth-first forest**.

Once DFS-forest for graph $G$ obtained, can classify edges.
- **tree** edges are edges in DFS-forest.
- **back** edges join vertex to ancestor
- **forward** edges not in tree, join vertex to descendant
- **cross** edges: all other edges.

Edge classification ambiguous for undirected graphs
- suppose that $e$ is edge that joins vertex $u$ to descendant $v$.
- $e$ is forward edge if DFS first considers $e$ from $u$.
- $e$ is back edge if DFS first considers $e$ from $v$.

> [!info] Theorem
> In an undirected graph, every edge is a tree edge or a back edge.
- a graph is connected if each pair of vertices joined by a path
- a cycle is a sequence of edges that start and end at same vertex
- articulation point is vertex whose removal disconnects the graph