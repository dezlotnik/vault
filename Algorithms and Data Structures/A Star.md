---
id: A Star
aliases:
  - A Star
  - A*
tags: []
---


# A Star

A* is a path finding and [[Graph Search]] algorithm. The algorithm works as
follows:
1. Initialize the open list.
2. Initialize the closed list.
3. Put the starting node on the open list.
4. While the open list is not empty, do the following:
    1. Find the node with the lowest `f = g + h` value in the open list.
    2. Pop the node off the open list.
    3. Find all neighbor nodes.
    4. For each neighbor node, do the following:
        1. If the node is in the closed-list, skip it.
        2. Compute `f`, `g`, and `h` values for the node.
        3. If the node isn't on the open list, make the current node it's parent
        and add it to the open list.
        3. If the node is already on the open list, check to see if this path is
        better. If so, change the parent and recalculate the `g` and `h` scores
        of the neighbor.
    5. Terminate the search if the open list is empty (no path exists), or if
    we've added the target node to the closed list.

