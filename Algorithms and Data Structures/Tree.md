---
id: Tree
aliases:
  - Tree
tags: []
---

# Tree
A tree is a nonlinear hierarchical data structure that consists of nodes
connected by edges. A tree can be thought of as an extension of a linked list
where a node can point to multiple other nodes. A tree must be connected and
cannot contain any cycles, i.e., no way to reach the same node twice.

A tree is a type of [[Graph]] with no cycles.

![[Pasted image 20231123170734.png|250]]

## Tree Traversal
Traversing a tree is visiting all the nodes once.
This is used for searching, inserting, and deleting nodes.

There are two types
- [[Depth First Search]]
- [[Breadth First Search]]

## Binary Tree
A binary tree is a tree where each node has at most two child nodes.

Depth first search for binary has three subtypes:
1. Pre-order Depth First Search
	1. Visit the root
	2. Traverse left subtree
	3. Traverse right subtree
2. In-order Depth First Search
	1. Traverse left subtree
	2. Visit the root
	3. Traverse right subtree
3. Post-order Depth First Search
	1. Traverse left subtree
	2. Traverse right subtree
	3. Visit the root

These have nice recursive implementations.

```python
def depth_first_search(tree):
    visit_order = list()
    def traverse(node):
        if node:
	        # This is pre-order
	        # swap the order to get in-order or
	        # post order
            # visit the node
            visit_order.append(node.get_value())
            # traverse left subtree
            traverse(node.get_left_child())
            # traverse right subtree
            traverse(node.get_right_child())
    
    traverse(tree.get_root())
    
    return visit_order
```

## Binary Search Tree
A binary search tree is a binary tree such that
- The left subtree of a node contains only nodes with values lesser than the
node’s value.
- The right subtree of a node contains only nodes with value greater than the
node’s value.
- The left and right subtree each must also be a binary search tree.
