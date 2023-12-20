---
id: Binary Search
aliases:
  - Binary Search
tags: []
---

# Binary Search

Binary search is an efficient method for finding an element in a *sorted*
array. The idea is to iteratively check the middle of the array, then throw out
the half of the array in which we know the element won't occur in.

> [!tip] Binary search has $O(log_2(n))$ time efficiency.
> The efficiency is $O(log_2(n))$ since in every iteration we cut the search
> space in half. Let $s$ be the number of steps it will take until the search
> space is cut down to 1. Then, $n * (1/2)^s = 1$, or $2^s = n$, which implies
> $s = log_2(n)$.

## Python implementation

```python
def binary_search(array, target, start, end):
    while end >= start:
        mid = start + (end - start)//2
        if (array[mid] == target):
            return mid
        if (array[mid] < target):
            start = mid + 1
        else:
            end = mid - 1
    return -1
```

```python
def binary_search(array, target):
    def binary_search_recursive(array, target, start_index, end_index):
        mid = start_index + (end_index - start_index)//2
        if (end_index < start_index):
            return -1
        if (array[mid] == target):
            return mid
        if (array[mid] < target):
            return binary_search_recursive(array, target, mid + 1, end_index)
        else:
            return binary_search_recursive(array, target, start_index, mid - 1)

    return binary_search_recursive(array, target, 0, len(array) - 1)
```
