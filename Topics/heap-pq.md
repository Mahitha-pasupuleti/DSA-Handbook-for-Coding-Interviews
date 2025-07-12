# Heap and Priority Queue Data Structures 🔺

## Introduction
A heap is a specialized tree-based data structure that satisfies the heap property. A priority queue is an abstract data type that operates similarly to a regular queue but with each element having a priority. Heaps are commonly used to implement priority queues.

## Core Concepts

### Important Terminologies
- **Heap**: Complete binary tree with heap property
- **Min Heap**: Parent nodes are smaller than or equal to children
- **Max Heap**: Parent nodes are larger than or equal to children
- **Priority Queue**: Queue where elements have priorities
- **Heapify**: Process of creating a heap from an array
- **Heap Property**: Relationship between parent and child nodes
- **Complete Binary Tree**: All levels filled except possibly last
- **Binary Heap**: Implementation using array
- **d-ary Heap**: Each node has d children

### Time Complexity Analysis
| Operation        | Average Case | Worst Case |
|-----------------|--------------|------------|
| Insert          | O(log n)     | O(log n)   |
| Delete Min/Max  | O(log n)     | O(log n)   |
| Get Min/Max     | O(1)         | O(1)       |
| Build Heap      | O(n)         | O(n)       |
| Heapify         | O(log n)     | O(log n)   |
| Decrease Key    | O(log n)     | O(log n)   |
| Increase Key    | O(log n)     | O(log n)   |

### Space Complexity
- **Binary Heap**: O(n) where n is number of elements
- **d-ary Heap**: O(n) but with different constant factors
- **Priority Queue**: O(n) based on heap implementation

## Implementation

### Basic Binary Heap
```python
class BinaryHeap:
    def __init__(self, max_heap=False):
        self.heap = []
        self.max_heap = max_heap
    
    def parent(self, i):
        return (i - 1) // 2
    
    def left_child(self, i):
        return 2 * i + 1
    
    def right_child(self, i):
        return 2 * i + 2
    
    def swap(self, i, j):
        self.heap[i], self.heap[j] = self.heap[j], self.heap[i]
    
    def insert(self, key):
        self.heap.append(key)
        self._sift_up(len(self.heap) - 1)
    
    def extract_top(self):
        if not self.heap:
            return None
        
        top = self.heap[0]
        last_elem = self.heap.pop()
        
        if self.heap:
            self.heap[0] = last_elem
            self._sift_down(0)
        
        return top
    
    def _sift_up(self, i):
        parent = self.parent(i)
        if self.max_heap:
            while i > 0 and self.heap[parent] < self.heap[i]:
                self.swap(i, parent)
                i = parent
                parent = self.parent(i)
        else:
            while i > 0 and self.heap[parent] > self.heap[i]:
                self.swap(i, parent)
                i = parent
                parent = self.parent(i)
    
    def _sift_down(self, i):
        size = len(self.heap)
        while True:
            largest = i if self.max_heap else i
            left = self.left_child(i)
            right = self.right_child(i)
            
            if self.max_heap:
                if left < size and self.heap[left] > self.heap[largest]:
                    largest = left
                if right < size and self.heap[right] > self.heap[largest]:
                    largest = right
            else:
                if left < size and self.heap[left] < self.heap[largest]:
                    largest = left
                if right < size and self.heap[right] < self.heap[largest]:
                    largest = right
            
            if largest == i:
                break
            
            self.swap(i, largest)
            i = largest
```

### Priority Queue using heapq
```python
import heapq

class PriorityQueue:
    def __init__(self):
        self._queue = []
        self._index = 0
    
    def push(self, item, priority):
        # Use negative priority for max heap
        heapq.heappush(self._queue, (priority, self._index, item))
        self._index += 1
    
    def pop(self):
        return heapq.heappop(self._queue)[-1]
    
    def peek(self):
        return self._queue[0][-1] if self._queue else None
    
    def is_empty(self):
        return len(self._queue) == 0
```

## Common Applications

### 1. K-th Largest Element
```python
def find_kth_largest(nums, k):
    heap = []
    for num in nums:
        heapq.heappush(heap, num)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]
```

### 2. Merge K Sorted Lists
```python
def merge_k_sorted_lists(lists):
    heap = []
    result = []
    
    # Initialize heap with first element from each list
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))
    
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        
        if elem_idx + 1 < len(lists[list_idx]):
            next_elem = lists[list_idx][elem_idx + 1]
            heapq.heappush(heap, (next_elem, list_idx, elem_idx + 1))
    
    return result
```

### 3. Running Median
```python
class MedianFinder:
    def __init__(self):
        self.small = []  # max heap
        self.large = []  # min heap
    
    def addNum(self, num):
        # Add to max heap
        heapq.heappush(self.small, -num)
        
        # Balance heaps
        if self.small and self.large and -self.small[0] > self.large[0]:
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)
        
        # Handle size difference
        if len(self.small) > len(self.large) + 1:
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)
        if len(self.large) > len(self.small) + 1:
            val = heapq.heappop(self.large)
            heapq.heappush(self.small, -val)
    
    def findMedian(self):
        if len(self.small) > len(self.large):
            return -self.small[0]
        if len(self.large) > len(self.small):
            return self.large[0]
        return (-self.small[0] + self.large[0]) / 2
```

## Edge Cases to Consider
1. Empty heap operations
2. Single element heap
3. Duplicate priorities
4. Equal elements
5. Negative priorities
6. Maximum capacity
7. Priority overflow/underflow
8. Concurrent access
9. Memory constraints
10. Large number of operations

## Common Pitfalls
1. Not maintaining heap property
2. Incorrect parent-child relationships
3. Array index errors
4. Not handling duplicates properly
5. Inefficient heapify implementation
6. Memory leaks
7. Priority inversion

## Practice Problems by Difficulty

### Easy
1. [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/) (LC #1046)
2. [Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/) (LC #703)
3. [Relative Ranks](https://leetcode.com/problems/relative-ranks/) (LC #506)

### Medium
1. [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) (LC #215)
2. [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) (LC #347)
3. [Task Scheduler](https://leetcode.com/problems/task-scheduler/) (LC #621)
4. [Ugly Number II](https://leetcode.com/problems/ugly-number-ii/) (LC #264)

### Hard
1. [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) (LC #295)
2. [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC #23)
3. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/) (LC #239)

## Real-World Applications
1. **Operating Systems**: Process scheduling
2. **Graph Algorithms**: Dijkstra's shortest path
3. **Data Compression**: Huffman coding
4. **Event-Driven Simulation**: Event scheduling
5. **Network Management**: Packet scheduling
6. **Database Systems**: Query optimization
7. **Load Balancing**: Task prioritization

## Advanced Topics
1. **Fibonacci Heap**:
   - Amortized complexity
   - Decrease key operation
2. **Binomial Heap**:
   - Multiple trees
   - Merge operation
3. **Pairing Heap**:
   - Simple implementation
   - Good practical performance
4. **Double-Ended Priority Queue**:
   - Min-max heap
   - Deap
5. **Concurrent Priority Queue**:
   - Lock-free implementation
   - Skip list based

## Important Resources
1. [Python heapq Documentation](https://docs.python.org/3/library/heapq.html)
2. [Binary Heap Implementation](https://www.geeksforgeeks.org/binary-heap/)
3. [Priority Queue Tutorial](https://www.programiz.com/dsa/priority-queue)
4. [Advanced Heap Structures](https://en.wikipedia.org/wiki/Heap_(data_structure))
5. [Fibonacci Heap Guide](https://www.geeksforgeeks.org/fibonacci-heap-set-1-introduction/)

## Interview Tips
1. Clarify heap type requirements
2. Consider built-in implementations
3. Handle edge cases explicitly
4. Analyze space-time tradeoffs
5. Consider custom comparators
6. Test with small examples
7. Optimize for specific operations
8. Consider thread safety needs