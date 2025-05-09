#ads 

### (Rooted) Binary Tree

A tree whose elements have at most 2 children is a **binary tree**
- typically named left and right child
- **rooted**: one node (root) designated as topmost node

Finite set of nodes which are either empty or consists of a root and two disjoint binary trees (left and right subtrees)
- root is single entry point, parentless
- every node has at most 2 children
- each non-root node has unique parent drawn above, each node's children drawn right below
- child-less nodes are **leaves**

Properties:
- **edge**: link from node to another
- **siblings**: two nodes with same parent
- **path length**: number of edges requiring traversal to get from node to another

Left $\neq$ right rule:
		**no right child**                                   **no left child**
![[Screenshot 2025-04-22 at 18.45.46.png]]
- these are two different trees

Size and depth:
- **size**: number of nodes in tree
- **depth** (node): distance of node from root
- **depth** (tree): depth of deepest node

Let $T$ be a rooted binary tree of height $h$. Then:
- $T$ has at most $2^{h+1}-1$ nodes
- $T$ has at most $2^h$ leaves

Binary trees can be used to represent binary trees
- leaves are variables/constants
- internal nodes operators

### Binary Trees for Data Storage

Similar concept to lists, each node has:
- pointer to parent (or NULL, or itself if root)
- pointer to left child (or NULL, or itself if no left child)
- pointer to right child (")
- item (or element)
- can be navigated like a list

Useful for dictionary operations
- **insert**: traverse existing tree according to fixed rules, insert new element in appropriate place
- **lookup**: traverse tree according to fixed rules
- **delete**: do lookup and, if found, delete (and fix tree structure if necessary)

Array-based representation:
- position $p$ can be represented by the single integer
- space usage depends on shape of tree
- some update operations cannot be efficiently supported
- deleting node + promoting child takes $O(n)$ time because all child descendants also move

### Binary Search Tree (BST)

Not good for some input sequences, can just use list:
- insert(x): append to list
- lookup(x): traverse list and return "TRUE" if found (maybe return location pointer)
- delete(x): first lookup, then splice out

A **binary search tree** is a tree where no node has more than two children, where it is true for **every node** **v** that **all elements** in the **left** subtree are **"smaller"** than **v** and **all elements** in the **right** subtree are **"larger"** than **v**.

### Tree Traversal

**Traversing a tree** is to visit each node in the tree exactly once.
- naturally recursive
- six possible ways to traverse the binary tree:

| 1     | 2     | 3     |
| ----- | ----- | ----- |
| root  | left  | right |
| root  | right | left  |
| left  | root  | right |
| left  | right | root  |
| right | root  | left  |
| right | left  | root  |
Types of traversals:
- **Preorder** traversal: root visited first
```PREORDER-TREE-WALK(x)
if x != NIL
	print x.key
	PREORDER-TREE-WALK(x.left)
	PREORDER-TREE-WALK(x.right)
```
- **Inorder** traversal: root visited between children
```INORDER-TREE-WALK(x)
if x != NIL
	INORDER-TREE-WALK(x.left)
	print x.key
	INORDER-TREE-WALK(x.right)
```
- **Postorder** traversal: root visited last
```POSTORDER-TREE-WALK(x)
if x != NIL
	POSTORDER-TREE-WALK(x.left)
	POSTORDER-TREE-WALK(x.right)
	print x.key
```

### Inorder Traversal: Sorting!

in BST:
- everything on left smaller
- everything on right larger

Inorder traversal:
- first recurses into left,
- then prints node,
- then recurses into right

Therefore:
- smallest elements printed first, then larger, then node, then bigger, then biggest
- traversal result sorts entire tree!

### Inserting into a BST

Call on root
- if match, return
- if new key smaller than current, insert on left
- else insert on right

```INSERT

class Node:
	...
	def insert(self, data):
		if data < self.data:
			if self.left is None:
				self.left = Node(data)
			else:
				self.left.insert(data)
		else:
			if self.right is None:
				self.right = Node(data)
			else:
				self.right.insert(data)
```

### Searching in a BST

Call on root
- if match, return
- if smaller than aim, go left
- else go right

```LOOKUP
class Node:
	...
	def lookup(self, data, parent=None):
		if data < self.data:
			if self.left is None:
				return None, None
			return self.left.lookup(data, self)
		elif data > self.data:
			if self.right is None:
				return None, None
			return self.right.lookup(data, self)
		else:
			return self, parent
```

### Deleting from BSTs

Deleting is most difficult operation
- first do lookup, if element not found then no further action
- else:
	- if node is leaf, then just remove
	- if node has one child, remove and replace with that one child
	- if node has two children, well fuck

```DELETE
class Node:
	...
	def children_count(self):
		if node is None:
			return None
		cnt = 0
		if self.left:
			cnt += 1
		if self.right:
			cnt += 1
		return cnt

	def delete(self, data):
		# get node containing data
		node, parent = self.lookup(data)
		if node is not None:
			children_count = node.children_count()
			if children_count == 0:
				# no children, just remove
				if parent.left is node:
					parent.left = None
				else:
					parent.right = None
				del node
			elif children_count == 1:
				# 1 child, replace node by child
				if node.left:
					n = node.left
				else:
					n = node.right
				if parent:
					if parent.left is node:
						parent.left = n
					else:
						parent.right = n
				del node
			else:
				# if node has 2 children, find successor
				parent = node
				successor = node.right
				while successor.left:
					parent = successor
					successor = successor.left
				# replace node data by successor data
				node.data = successor.data
				# fix successor's parent's child
				if parent.left == successor:
					parent.left = successor.right
				else:
					parent.right = successor.right
```

### Traversing BST

Always **inorder** traversal

```PRINT_TREE
class Node:
	...
	def print_tree(self):
		if self.left:
			self.left.print_tree()
		print self.data
		if self.right:
			self.right.print_tree()
```

### BST Complexity

$O(h)$ - searching, insertions, deletions
- $O(\log n)$ in average case
- in worst case, degenerates to $O(N)$
	- can be avoided by using balanced trees (AVL or red-black)