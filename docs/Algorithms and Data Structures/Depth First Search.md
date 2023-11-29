---
id: Depth First Search
aliases:
  - Depth First Search
tags: []
---

# Depth First Search

Similar to [[Breadth First Search]] except we use a [[Stack]] instead of a 
[[Queue]] as the data structure that holds nodes not yet visited. Since a
stack is Last-In-First-Out, when we add a child node to the stack, we will 
visit that child node on the next iteration.

The algorithm works as follows:

1. Start by putting any one of the graph's vertices on the stack.
2. Take the front item off the stack and add it to the visited list.
3. Create a list of that vertex's adjacent nodes. Add the ones which aren't in
the visited list onto the stack.
4. Keep repeating steps 2 and 3 until the queue is empty.


```python
stack = [start_node]
visited = [ ]

while (stack):
	curr_node = stack[-1]
	visited.append(curr_node)
	neighbors = getNeighbors(curr_node)
	for neighbor in neighbors:
		if (not neighbors in visited):
			stack.append(neighbor)
```

See also [[Tree#Binary Tree]]. 

