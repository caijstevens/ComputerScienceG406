#ads 

### Balanced BST

If BST is **balanced**, $h = O(\log n)$ - **okay**
- if BST is **degenerated**, $h = \Omega(n)$ - **bad**

**Rotations** (basic re-balancing operations):
- local operation - modifies constant number of links ($O(1)$ time)
- preserves BST property
- can be left or right

simple rotations can be combined to provide re-balancing
- when applied to a triple parent-child-grandchild this is called **trinode restructuring**
- depends on whether child and grandchild are on same side

### AVL Trees

An **AVL tree** is a self-balancing BST with following property:
- for each node $v$, heights of $v$'s children differ by at most 1
- height of NULL is 0, height of proper leaf is 1
- height of parent = max height of child + 1

Proof: The **height** of an AVL tree storing $n$ keys is $O(\log n)$.
- first bound $n(h)$ (minimum number of internal nodes of AVL tree of height $h$)
- $n(1) = 1$ and $n(2) = 2$.
- For $n > 2$, tree of height $h$ contains root node, one subtree of height $n-1$ and another of height $n-2$.
- shown as $n(h) = 1 + n(h-1) + n(h-2)$.
- knowing $n(h-1) > n(h-2)$, we get $n(h) > 2n(h-2)$.
- $n(h) > 2^{h/2-1}$
- $h < 2\log n(h) + 2$
- $\log(n) \geq \log(n(h))$ therefore height of AVL tree is $O(\log n)$.

### Other BST Operations

Insertion and deletion can violate height-balance property
- trinode restructuring can be useful

### Insertion

4 cases for insertion:
- let node that needs rebalancing be $\alpha$.
	1. insertion into **left** subtree of **left** child of $\alpha$ = right rotation
	2. insertion into **right** subtree of **right** child of $\alpha$ = left rotation
	3. insertion into **right** subtree of **left** child of $\alpha$ = left-right rotation (double)
	4. insertion into **left** subtree of **right** child of $\alpha$ = right-left rotation (double)
		
| subtree | child | rotation(s) |
| ------- | ----- | ----------- |
| left    | left  | right       |
| left    | right | right-left  |
| right   | left  | left-right  |
| right   | right | left        |
Post-insertion fix up:
- if $p$ is inserted node, nodes with heights changed are only between $p$ and root
- from $p$, go up towards root, find first unbalanced node $z$
	- if $z$ not found, height balance not violated
	- if found, let $y$ and $x$ be the child and grandchild of $z$ on the path to $p$
	- do trinode restructuring on $z$ - $y$ - $x$
- height balance restored

### Deletion

Standard BST deletion can violate height-balance property
- again trinode restructuring is useful here
- let z be first unbalanced node on the path
- let y be taller child of z
- let x be taller child of y (or if children of y have same height, on same left/right side as y)
- use trinode restructuring on z - y - x.

> [!important] ISSUE NOTICE:
> this will fix up the subtree of z but may reduce its height and cause other issues. must keep going up the tree and do restructuring whenever unbalanced node met.

Standard deletion in AVL trees is $O(\log n)$.
- fix-up uses $O(1)$ time per level.
- done $\leq 1$ time per level, height is $O(\log n)$

Insertion-deletion processing can be unified
- both trace upward path from some node
- both use trinode restructuring

"Early stop" condition: can stop post-processing when:
- reach ancestor whose height didn't change
- trinode restructing results in same height as before (can store old height to confirm)

### Performance Summary

AVL tree storing $n$ items
- data structure uses $O(n)$ space
- single restructure takes $O(1)$ time
- searching takes $O(\log n)$ time
- insertion takes $O(\log n)$ time
- removal takes $O(\log n)$ time