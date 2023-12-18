---
id: Bubble Sort
aliases:
  - Bubble Sort
tags: []
---

# Bubble Sort

Bubbble sort is a simple sorting algorithm that iteratively compares two
adjacent elements and swaps them if they are in the wrong order. On a single
iteration the largest value will "bubble" to the top of the array.

> [!tip] Bubble sort has O(n^2) time complexity.

## Python Implementation 

```python
def bubble_sort(l):
    end_index = len(l) - 1
    while end_index > 0:
        for i in range(0, end_index):
            curr = l[i]
            next = l[i+1]
            if (curr > next):
                l[i] = next
                l[i+1] = curr
        end_index -= 1
```
