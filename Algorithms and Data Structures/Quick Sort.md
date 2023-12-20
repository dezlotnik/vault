---
id: Quick Sort
aliases:
  - Quick Sort
tags: []
---


# Quick Sort

Quick sort is a *divide and conquer* sorting algorithm that works as follows:
1. Pick a pivot point in the list.
2. Place every value smaller than the pivot value to the left and every value
greater than the pivot to the right of the pivot point.
3. Recursively repeat steps 1 and 2 for each sublists to the left and right
of the pivot point.

> [!tip] Efficiency
> Quick sort has average $O(nlog_2(n))$ time efficiency, but maximum efficiency
> of $O(n^2)$. Quick sort is an in-place sorting algorithm, so it will have
> $O(1)$ space complexity.

## Python Implementation

```python
def sort_pivot_point(items, start_index, end_index):
    pivot_index = end_index
    pivot_value = items[pivot_index]
    left_index = start_index
    while left_index != pivot_index:
        compare_value = items[left_index]
        if compare_value <= pivot_value:
            # increment index and continue
            left_index += 1
            continue
        
        items[left_index] = items[pivot_index - 1]
        items[pivot_index - 1] = pivot_value
        items[pivot_index] = compare_value
        pivot_index -= 1
    return pivot_index

def quick_sort(items, start_index = 0, end_index = len(items) - 1):
    if start_index >= end_index:
        # termination condition, a single element exists in the sublist.
        return
    # sort pivot, this places the pivot point at it's correct position in the
    # list.
    pivot_index = sort_pivot_point(items, start_index, end_index)
    # sort left of pivot
    quick_sort(items, start_index, pivot_index - 1)
    # sort right of pivot
    quick_sort(items, pivot_index + 1, end_index)
```
