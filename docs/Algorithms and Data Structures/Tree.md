A tree is a nonlinear hierarchical data structure that consists of nodes connected by edges. A tree can be thought of as an extension of a linked list where a node can point to multiple other nodes. A tree must be connected and cannot contain any cycles, i.e., no way to reach the same node twice.

A tree is a type of [[Graph]] with no cycles.

![[Pasted image 20231123170734.png|250]]
# Tree Traversal
Traversing a tree is visiting all the nodes once.
This is used for searching, inserting, and deleting nodes.

There are two types
- [[Depth First Search]]
- [[Breadth First Search]]

Depth first search has three subtypes:
1. Pre-order Depth First Search
2. In-order Depth First Search
3. Post-order Depth First Search

# Binary Tree
A binary tree is a tree where each node has at most two child nodes.

# Binary Search Tree
A binary search tree is a binary tree such that
- The left subtree of a node contains only nodes with values lesser than the node’s value.
- The right subtree of a node contains only nodes with value greater than the node’s value.
- The left and right subtree each must also be a binary search tree.