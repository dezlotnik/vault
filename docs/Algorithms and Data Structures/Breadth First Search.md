Similar to [[Depth First Search]], but we use a [[Queue]] instead of a [[Stack]].

The algorithm works as follows:

1. Start by putting any one of the graph's vertices at the back of a queue.
2. Take the front item of the queue and add it to the visited list.
3. Create a list of that vertex's adjacent nodes. Add the ones which aren't in the visited list to the back of the queue.
4. Keep repeating steps 2 and 3 until the queue is empty.


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
