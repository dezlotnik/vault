---
id: Breadth First Search
aliases:
  - Breadth First Search
tags: []
---

# Breadth First Search

Breadth first search is a [[Graph Search]] algorithm. It can also used for
[[Tree]] traversal.
It is similar to [[Depth First Search]], but we use a [[Queue]] instead of a
[[Stack]].
Since a [[Queue]] is a FIFO structure, we will visit all children of a visited
node before visiting the "grandchildren".

The algorithm works as follows:

1. Start by putting any one of the graph's vertices at the back of a queue.
2. Take the front item off the queue and add it to the visited list.
3. Create a list of that vertex's adjacent nodes. Add the ones which aren't in
the visited list to the back of the queue.
4. Keep repeating steps 2 and 3 until the queue is empty.

Breadth first search for [[Tree]] traversal is similar, however we don't need
to keep track of visited nodes since a [[Tree]] will contain no cycles.

```python
queue = [start_node]
visited = [ ]

while (queue):
	curr_node = queue.pop()
	visited.append(curr_node)
	neighbors = getNeighbors(curr_node)
	for neighbor in neighbors:
		if (not neighbors in visited):
			queue.append(neighbor)
```
