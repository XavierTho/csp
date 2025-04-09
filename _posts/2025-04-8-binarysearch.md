---
layout: post
title: Binary Search Homework
toc: False
comments: True
---

# Binary Search Homework Hacks

## Homework Hack 1: Binary Search on a Rotated Array

**Description**:  
You are given a sorted array that has been rotated at some unknown pivot. Write a function that uses Binary Search to find a target element in this rotated array. If the element is found, return its index. If not, return -1.

**Example**:

**Input**:
```python
arr = [4, 5, 6, 7, 0, 1, 2]
target = 1
```

**Output**:
```
5
```

**Solution**:
```python
def search_rotated_array(arr, target):
    left, right = 0, len(arr) - 1

    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid

        # Left half is sorted
        if arr[left] <= arr[mid]:
            if arr[left] <= target < arr[mid]:
                right = mid - 1
            else:
                left = mid + 1
        # Right half is sorted
        else:
            if arr[mid] < target <= arr[right]:
                left = mid + 1
            else:
                right = mid - 1

    return -1
```

---

## Homework Hack 2: Find the First and Last Occurrence of an Element

**Description**:  
Write a function that uses binary search to find the first and last occurrence of a given target element in a sorted array. If the element is not present, return -1.

**Example**:

**Input**:
```python
arr = [1, 2, 2, 2, 3, 4, 5]
target = 2
```

**Output**:
```
(1, 3)
```

**Solution**:
```python
def find_first_last(arr, target):
    def binary_search(is_first):
        left, right = 0, len(arr) - 1
        result = -1
        while left <= right:
            mid = (left + right) // 2
            if arr[mid] == target:
                result = mid
                if is_first:
                    right = mid - 1
                else:
                    left = mid + 1
            elif arr[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return result

    first = binary_search(True)
    last = binary_search(False)

    if first == -1:
        return -1
    return (first, last)
```

---

## Homework Hack 3: Search for the Smallest Element ≥ Target

**Description**:  
You are given a sorted array of integers. Write a function that uses Binary Search to find the smallest element that is greater than or equal to the target. If such an element doesn't exist, return -1.

**Example**:

**Input**:
```python
arr = [1, 3, 5, 7, 9, 11]
target = 8
```

**Output**:
```
9
```

**Solution**:
```python
def smallest_ge(arr, target):
    left, right = 0, len(arr) - 1
    result = -1

    while left <= right:
        mid = (left + right) // 2
        if arr[mid] >= target:
            result = arr[mid]
            right = mid - 1
        else:
            left = mid + 1

    return result if result != -1 else -1
```
