---
id: Merge Sort
aliases:
  - Merge Sort
tags: []
---

# Merge Sort

Merge sort is a *divide and conquer* sorting algorithm that works as follows:
1. Divide the list into equal halves until each sublist has a single element.
2. Merge the sublists into ordered sublists until the entire list has been
reassembled.

> [!tip] Efficiency
> Merge sort has $O(nlog_2(n))$ time efficiency. 

## Python Implementation

```python
def divide(items):
    mid = len(items)//2
    return items[:mid], items[mid:]
    
def merge(left, right):
    left_index = 0
    right_index = 0
    merged = []
    while left_index < len(left) and right_index < len(right):
        if (left[left_index] < right[right_index]):
            merged.append(left[left_index])
            left_index += 1
        else:
            merged.append(right[right_index])
            right_index += 1
    # We've gone through all of left or all or right.
    # Append the remainder onto the merged list.
    # left_index = len(left) or right_index = len(right)
    merged += left[left_index:]
    merged += right[right_index:]
    return merged
    
def mergesort(items):
    # Step 1: base case
    if len(items) <= 1:
        return items
    
    # Step 2: divide items
    list1, list2 = divide(items)
    
    # Step 3: Merge sort
    left = mergesort(list1)
    right = mergesort(list2)
    
    return merge(left, right)
```
