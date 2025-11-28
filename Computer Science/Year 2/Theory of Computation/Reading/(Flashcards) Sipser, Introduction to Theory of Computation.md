#toc #flashcards/toc/Sipser/SequencesAndTuples 

What is a **sequence**?::A **sequence** of objects is a list of these objects in some order.
<!--SR:!2025-07-15,3,250-->
What name is often given to a finite sequence?::**Tuple**. A sequence with $k$ elements is a $k$-**tuple**.
<!--SR:!2025-07-15,3,250-->
What is the **power set** of $A$?::The power set of $A$ is the set of all subsets of $A$.
What is the **Cartesian product** of $A$ and $B$?::The **Cartesian product** (or cross product) of $A$ and $B$ written $A \times B$, is the set of all pairs wherein the first element is a member of $A$ and the second element is a member of $B$.

#flashcards/toc/Sipser/FunctionsAndRelations 

Define a **function**.::A **function** is an object that sets up an input-output relationship.
<!--SR:!2025-09-16,1,230-->
What is special about a function's input and output?::In every function, the same input always produces the same output.
<!--SR:!2025-09-18,3,250-->
Define the **domain** and **range** of a function.::The **domain** is the set of possible inputs to a function. The **range** is the set of possible outputs from a function.
<!--SR:!2025-09-19,4,270-->
What is a $k$-ary function?::A $k$**-ary** function is a function with $k$ arguments.
<!--SR:!2025-09-16,1,230-->
What is the **arity** of a function?::The **arity** of a function is the number of arguments a function has.
<!--SR:!2025-09-16,1,230-->
What two names can be given to a function whose range is $\{\text{TRUE , FALSE}\}$?::A **predicate** or **property**.
<!--SR:!2025-09-16,1,230-->
What is a relation?::A **relation** is a property whose domain is a set of $k$-tuples $A\times\dots\times A$. Can also be called a $k$-ary relation or a $k$-ary relation on $A$.
<!--SR:!2025-09-16,1,230-->
What is an **equivalence relation**?::An **equivalence relation** captures the notion of two objects being equal in some feature.
<!--SR:!2025-09-16,1,230-->
What conditions do an equivalence relation satisfy?:: **Reflexivity** (for every $x$, $xRx$), **Symmetry** (for every $x$ and $y$, $xRy \rightarrow yRx$) and **Transitivity** (for every $x, y$ and $z$, $xRy \land yRx \rightarrow xRz$).
<!--SR:!2025-09-16,1,230-->

#flashcards/toc/Sipser/Graphs

What is an undirected graph?::A graph or undirected graph is a set of points with lines connecting some of the points.
<!--SR:!2025-09-18,3,250-->
What are the different key parts of a graph?::The **nodes** (or vertices) and the **edges**.
<!--SR:!2025-09-19,4,270-->
What is the **degree** of a particular node?::The degree of a node is the number of edges at that node. No more than one edge is allowed between any two nodes.
<!--SR:!2025-09-18,3,250-->
What makes a graph undirected?::The order of $i$ and $j$ in the pair $(i,j)$ doesn't affect the representation of the graph, meaning that pairs $(i,j)$ and $(j,i)$ represent the same edge.
<!--SR:!2025-09-18,3,250-->
What would make graph $G$ a subgraph of graph $H$?::The nodes of $G$ must be a subset of the nodes of $H$, and the edges of $G$ are the edges of $H$ on the corresponding nodes.
What is a path?::A **path** in a graph is a sequence of nodes connected by edges. A **simple path** is a path that doesn't repeat any nodes.
What does it mean if a graph is **connected**?::A graph is **connected** if every two nodes have a path between them.
<!--SR:!2025-09-16,1,230-->
What makes a path a **cycle**?::A path is a **cycle** if it starts and ends in the same node. A **simple cycle** is one that contains at least three nodes and repeats only the first and last nodes.
<!--SR:!2025-09-16,1,230-->
What is a **tree**?::A **tree** is a graph that is connected and contains no simple cycles.
<!--SR:!2025-09-16,1,230-->
What is the **root** of a tree?::The **root** is a specially designated node that may appear in a tree.
<!--SR:!2025-09-18,3,250-->
What are the **leaves** of a tree?::The **leaves** of the tree are the nodes of degree 1 in a tree (excluding the root).
<!--SR:!2025-09-18,3,250-->
What makes a graph directed?::A graph is **directed** if it has arrows between the nodes instead of lines.
<!--SR:!2025-09-18,3,250-->
What is the **outdegree** and **indegree** of a node in a directed graph?::The outdegree is the number of arrows pointing from a particular node, and the indegree is the number of arrows pointing to a particular node.
<!--SR:!2025-09-18,3,250-->
What is a **directed path**?::A directed path is one in which all the arrows point in the same direction as its steps.
<!--SR:!2025-09-16,1,230-->
What makes a directed graph **strongly connected**?::A directed graph is strongly connected if a directed path connects every two nodes.

#flashcards/toc/Sipser/StringsAndLanguages

What is an **alphabet**?::An alphabet is a nonempty finite set, the members of which being the **symbols** of the alphabet.
What is a **string over an alphabet**?::A finite sequence of symbols from that alphabet written next to each other and not separated by commas.
What is the **length** of a string over an alphabet?::The number of symbols in that string. Also written $|w|$ where $w$ is the string over an alphabet.
What is the **empty string**?::The string of length zero. Written $\epsilon$.
What is the **reverse** of a string?::The reverse of a string $w$, written $w^R$ is the string obtained by writing $w$ in the opposite order. ($w_nw_{n-1}\dots w_1$)
What is a **substring**?::A string $z$ is a substring of another string $w$ if $z$ appears consecutively within $w$.
What is a **concatenation**?::The **concatenation** of strings $x$ and $y$, written $xy$, is the string obtained by appending $y$ to the end of $x$, as in $x_1\dots x_my_1\dots y_n$.
What is a **language**?::A language is a set of strings.

#flashcards/toc/Sipser/BooleanLogic

What is **Boolean logic**?::Boolean logic is a mathematical system built around the two values TRUE and FALSE.
<!--SR:!2025-09-16,1,230-->
What are the three primary Boolean operations?::**Negation** (NOT, $\lnot$), **Conjunction** (AND, $\land$), and **Disjunction** (OR, $\lor$).
<!--SR:!2025-09-19,4,270-->
What is the **distributive law**?::$a\times(b+c) = (a\times b)+(a\times c)$.
<!--SR:!2025-09-16,1,230-->
Which Boolean operations are **sufficient and necessary** to express all Boolean operations?::AND and NOT.
<!--SR:!2025-09-18,3,250-->

