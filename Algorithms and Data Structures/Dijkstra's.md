---
id: Dijkstra's
aliases:
  - Dijkstra's
  - Dijkstra's Algorithm
tags: []
---

# Dijkstra's Algorithm

Dijkstra's Algorithm is a [[Greedy Algorithm]] used for finding the shortest
path between two nodes in a [[Graph]].

The algorithm is as follows:
1. Initialize a distances data structure to keep track of all distances from the
source node to each node. Set the distance to source equal to zero and all other
distances equal to infinity.
2. All all nodes to a minimum priority queue.
3. Initialize a visitied data structure to keep track of which nodes have been
visited.
4. While the queue is not empty, pop out the node with the minimum distance.
5. Add the node to visited.
6. Update the distances of all adjacent nodes.
    1. If the distance of current + the distance from current to
    adjacent is less than adjacent's distance, then update adjacent's distance.
    2. Otherwise, do nothing.

## Python Implementation

```python
def dijkstra(graph, start_node, end_node):
    queue = []
    distances = dict()
    prev = dict()
    visited = set()
    
    # Add all nodes to the distances dict and assign inf distance.
    # Also add all nodes to the queue
    for node in graph.nodes:
        if node is start_node:
            distances[node] = 0
        else:
            distances[node] = float("inf")
        prev[node] = node
        queue.append(node)
        
    while queue:
        # sort the queue
        queue.sort(key = lambda x: distances[x])
        
        # pop out the node with the smallest distance
        node = queue.pop(0)
        
        # add the node to visited
        visited.add(node)
        
        for edge in node.edges:
            if not edge.node in visited:
                # update distance
                new_distance = distances[node] + edge.distance
                if new_distance < distances[edge.node]:
                    distances[edge.node] = new_distance
                    prev[edge.node] = node

    # Build the path
    node = end_node
    path = [end_node.value]
    while node != start_node:
        path.insert(0, prev[node].value)
        node = prev[node]
    
    return distances[end_node], path
```
