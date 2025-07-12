# Sorting Algorithms 🔃

## Introduction
Sorting is the process of arranging elements in a specific order, typically in ascending or descending order. Understanding sorting algorithms is crucial as they form the basis for many other algorithms and are frequently used in real-world applications.

## Core Concepts

### Important Terminologies
- **In-place Sorting**: Algorithm uses O(1) extra space
- **Stable Sorting**: Preserves relative order of equal elements
- **Comparison Sort**: Uses element comparisons to sort
- **Non-comparison Sort**: Uses element properties to sort
- **Adaptive Sort**: Performance improves with presorted data
- **Internal Sort**: All data fits in main memory
- **External Sort**: Data needs to be retrieved from external storage
- **Natural Sort**: Exploits existing order in the data
- **Hybrid Sort**: Combines multiple sorting algorithms

### Time and Space Complexity Analysis
| Algorithm      | Best       | Average   | Worst      | Space     | Stable | In-place |
|---------------|------------|-----------|------------|-----------|---------|----------|
| Bubble Sort   | O(n)       | O(n²)     | O(n²)      | O(1)      | Yes     | Yes      |
| Selection Sort| O(n²)      | O(n²)     | O(n²)      | O(1)      | No      | Yes      |
| Insertion Sort| O(n)       | O(n²)     | O(n²)      | O(1)      | Yes     | Yes      |
| Merge Sort    | O(n log n) | O(n log n)| O(n log n) | O(n)      | Yes     | No       |
| Quick Sort    | O(n log n) | O(n log n)| O(n²)      | O(log n)  | No      | Yes      |
| Heap Sort     | O(n log n) | O(n log n)| O(n log n) | O(1)      | No      | Yes      |
| Counting Sort | O(n + k)   | O(n + k)  | O(n + k)   | O(k)      | Yes     | No       |
| Radix Sort    | O(d(n + k))| O(d(n + k))| O(d(n + k))| O(n + k) | Yes     | No       |
| Shell Sort    | O(n log n) | O(n^1.3)  | O(n²)      | O(1)      | No      | Yes      |
| Tim Sort      | O(n)       | O(n log n)| O(n log n) | O(n)      | Yes     | No       |

Where:
- n = number of elements
- k = range of elements
- d = number of digits

## Implementation

### 1. Quick Sort
```python
def quick_sort(arr, low, high):
    def partition(low, high):
        pivot = arr[high]
        i = low - 1
        
        for j in range(low, high):
            if arr[j] <= pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]
        
        arr[i + 1], arr[high] = arr[high], arr[i + 1]
        return i + 1
    
    if low < high:
        pi = partition(low, high)
        quick_sort(arr, low, pi - 1)
        quick_sort(arr, pi + 1, high)
```

### 2. Merge Sort
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

### 3. Heap Sort
```python
def heap_sort(arr):
    def heapify(n, i):
        largest = i
        left = 2 * i + 1
        right = 2 * i + 2
        
        if left < n and arr[left] > arr[largest]:
            largest = left
        if right < n and arr[right] > arr[largest]:
            largest = right
        
        if largest != i:
            arr[i], arr[largest] = arr[largest], arr[i]
            heapify(n, largest)
    
    n = len(arr)
    
    # Build max heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(n, i)
    
    # Extract elements from heap
    for i in range(n - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(i, 0)
```

### 4. Counting Sort
```python
def counting_sort(arr):
    if not arr:
        return arr
    
    # Find range of array elements
    max_val = max(arr)
    min_val = min(arr)
    range_val = max_val - min_val + 1
    
    # Initialize counting array and output array
    count = [0] * range_val
    output = [0] * len(arr)
    
    # Store count of each element
    for num in arr:
        count[num - min_val] += 1
    
    # Modify count array to store actual positions
    for i in range(1, len(count)):
        count[i] += count[i - 1]
    
    # Build output array
    for num in reversed(arr):
        index = count[num - min_val] - 1
        output[index] = num
        count[num - min_val] -= 1
    
    return output
```

## Common Techniques

### 1. Three-Way Partitioning (Dutch National Flag)
```python
def sort_colors(nums):
    low = mid = 0
    high = len(nums) - 1
    
    while mid <= high:
        if nums[mid] == 0:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == 1:
            mid += 1
        else:  # nums[mid] == 2
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
```

### 2. Custom Comparator
```python
def custom_sort(arr):
    return sorted(arr, key=lambda x: (priority(x), x))

# Example: Sort strings by length then lexicographically
strings = ["banana", "apple", "cherry"]
sorted_strings = sorted(strings, key=lambda x: (len(x), x))
```

## Edge Cases to Consider
1. Empty array
2. Single element array
3. Array with all identical elements
4. Array already sorted
5. Array sorted in reverse
6. Array with negative numbers
7. Array with floating point numbers
8. Very large arrays
9. Arrays with duplicates
10. Arrays with special characters

## Common Pitfalls
1. Not handling empty or single-element arrays
2. Incorrect pivot selection in QuickSort
3. Stack overflow in recursive implementations
4. Not considering stability requirements
5. Inefficient handling of duplicates
6. Memory leaks in implementations
7. Incorrect boundary conditions

## Practice Problems by Difficulty

### Easy
1. [Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/) (LC #905)
2. [Height Checker](https://leetcode.com/problems/height-checker/) (LC #1051)
3. [Sort Array by Increasing Frequency](https://leetcode.com/problems/sort-array-by-increasing-frequency/) (LC #1636)

### Medium
1. [Sort Colors](https://leetcode.com/problems/sort-colors/) (LC #75)
2. [Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/) (LC #451)
3. [Custom Sort String](https://leetcode.com/problems/custom-sort-string/) (LC #791)
4. [Sort the Matrix Diagonally](https://leetcode.com/problems/sort-the-matrix-diagonally/) (LC #1329)

### Hard
1. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)
2. [Maximum Gap](https://leetcode.com/problems/maximum-gap/) (LC #164)
3. [Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) (LC #315)

## Real-World Applications
1. **Database Systems**: Indexing and query optimization
2. **File Systems**: File organization
3. **Operating Systems**: Process scheduling
4. **Graphics**: Rendering order
5. **Text Processing**: Dictionary ordering
6. **Network Routing**: Packet scheduling
7. **Computational Biology**: Genome sequencing

## Advanced Topics
1. **External Sorting**:
   - Multi-way merge
   - Replacement selection
2. **Parallel Sorting**:
   - Parallel merge sort
   - Bitonic sort
3. **Specialized Sorting**:
   - Network sorting
   - Pancake sorting
4. **String Sorting**:
   - Radix sort variations
   - Suffix arrays
5. **Online Sorting**:
   - Insertion streams
   - Priority queues

## Important Resources
1. [Sorting Algorithms Visualizations](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)
2. [Python's Timsort Implementation](https://github.com/python/cpython/blob/main/Objects/listsort.txt)
3. [Comparison of Sorting Algorithms](https://www.geeksforgeeks.org/comparison-of-different-sorting-algorithms/)
4. [External Sorting Tutorial](https://www.geeksforgeeks.org/external-sorting/)
5. [Parallel Sorting Algorithms](https://www.geeksforgeeks.org/parallel-sorting-algorithms/)

## Interview Tips
1. Clarify input constraints
2. Consider stability requirements
3. Analyze space complexity needs
4. Choose appropriate algorithm
5. Handle edge cases explicitly
6. Consider optimization opportunities
7. Test with small examples
8. Discuss trade-offs between algorithms