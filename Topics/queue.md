# Queue Data Structure ⏩

## Introduction
A queue is a fundamental data structure that follows the First-In-First-Out (FIFO) principle. Think of it like a line of people waiting - the first person to join the line is the first one to be served.

## Core Concepts

### Important Terminologies
- **Queue**: A FIFO (First-In-First-Out) data structure
- **Enqueue**: Operation to add an element to the back of queue
- **Dequeue**: Operation to remove an element from the front of queue
- **Front/Head**: First element in the queue
- **Rear/Tail**: Last element in the queue
- **Deque**: Double-ended queue allowing operations at both ends
- **Priority Queue**: Queue where elements have priorities
- **Circular Queue**: Fixed-size queue implemented circularly

### Time Complexity Analysis
| Operation | Average Case | Worst Case |
|-----------|--------------|------------|
| Enqueue   | O(1)         | O(1)       |
| Dequeue   | O(1)         | O(1)       |
| Peek      | O(1)         | O(1)       |
| Search    | O(n)         | O(n)       |
| isEmpty   | O(1)         | O(1)       |

### Space Complexity
- **Basic Queue**: O(n) where n is number of elements
- **Circular Queue**: O(n) where n is fixed size
- **Priority Queue**: O(n) for binary heap implementation

## Implementation

### Basic Queue Implementation
```python
class Queue:
    def __init__(self):
        self.items = []
    
    def enqueue(self, item):
        self.items.append(item)
    
    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)
        raise IndexError("Dequeue from empty queue")
    
    def front(self):
        if not self.is_empty():
            return self.items[0]
        raise IndexError("Front from empty queue")
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)
```

### Circular Queue Implementation
```python
class CircularQueue:
    def __init__(self, size):
        self.size = size
        self.queue = [None] * size
        self.front = self.rear = -1
    
    def enqueue(self, item):
        if self.is_full():
            raise Exception("Queue is full")
        
        if self.front == -1:
            self.front = 0
        self.rear = (self.rear + 1) % self.size
        self.queue[self.rear] = item
    
    def dequeue(self):
        if self.is_empty():
            raise Exception("Queue is empty")
        
        item = self.queue[self.front]
        if self.front == self.rear:
            self.front = self.rear = -1
        else:
            self.front = (self.front + 1) % self.size
        return item
    
    def is_empty(self):
        return self.front == -1
    
    def is_full(self):
        return (self.rear + 1) % self.size == self.front
```

### Deque Implementation
```python
from collections import deque

class Deque:
    def __init__(self):
        self.items = deque()
    
    def add_front(self, item):
        self.items.appendleft(item)
    
    def add_rear(self, item):
        self.items.append(item)
    
    def remove_front(self):
        return self.items.popleft()
    
    def remove_rear(self):
        return self.items.pop()
    
    def is_empty(self):
        return len(self.items) == 0
```

## Common Applications

### 1. BFS Implementation
```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    
    while queue:
        vertex = queue.popleft()
        print(vertex, end=' ')
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### 2. Sliding Window Maximum
```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    window = deque()
    
    for i in range(len(nums)):
        # Remove elements outside current window
        while window and window[0] < i - k + 1:
            window.popleft()
        
        # Remove smaller elements
        while window and nums[window[-1]] < nums[i]:
            window.pop()
        
        window.append(i)
        
        if i >= k - 1:
            result.append(nums[window[0]])
    
    return result
```

## Common Patterns

### 1. Level Order Traversal
```python
def level_order_traversal(root):
    if not root:
        return []
    
    result = []
    queue = deque([root])
    
    while queue:
        level = []
        level_size = len(queue)
        
        for _ in range(level_size):
            node = queue.popleft()
            level.append(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(level)
    
    return result
```

### 2. Task Scheduling
```python
def task_scheduling(tasks, n):
    from collections import Counter
    counter = Counter(tasks)
    max_freq = max(counter.values())
    max_freq_tasks = sum(1 for v in counter.values() if v == max_freq)
    
    return max(len(tasks), (max_freq - 1) * (n + 1) + max_freq_tasks)
```

## Edge Cases to Consider
1. Empty queue operations
2. Queue with single element
3. Queue reaching maximum capacity
4. Circular queue wrap-around
5. Priority conflicts in priority queue
6. Deque operations at both ends
7. Multiple elements with same priority

## Common Pitfalls
1. Not handling empty queue
2. Incorrect circular queue indexing
3. Memory leaks in custom implementations
4. Not maintaining FIFO order
5. Inefficient array-based implementation

## Practice Problems by Difficulty

### Easy
1. [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) (LC #232)
2. [Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/) (LC #933)
3. [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/) (LC #387)

### Medium
1. [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/) (LC #622)
2. [Perfect Squares](https://leetcode.com/problems/perfect-squares/) (LC #279)
3. [Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC #200)
4. [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) (LC #994)

### Hard
1. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/) (LC #239)
2. [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) (LC #295)
3. [Maximum Performance of a Team](https://leetcode.com/problems/maximum-performance-of-a-team/) (LC #1383)

## Real-World Applications
1. **Job Scheduling**: Process and task management
2. **Printer Queue**: Document printing order
3. **Web Servers**: Request handling
4. **BFS Applications**: GPS navigation, social networks
5. **Cache Implementation**: LRU cache

## Advanced Topics
1. **Priority Queue Implementations**:
   - Binary Heap
   - Fibonacci Heap
   - Binomial Heap
2. **Specialized Queues**:
   - Double-ended Priority Queue
   - Multi-level Queue
   - Blocking Queue
3. **Concurrent Queue Implementation**

## Important Resources
1. [Python collections.deque](https://docs.python.org/3/library/collections.html#collections.deque)
2. [Queue Data Structure](https://www.geeksforgeeks.org/queue-data-structure/)
3. [Priority Queue Tutorial](https://www.programiz.com/dsa/priority-queue)
4. [Circular Queue Guide](https://www.programiz.com/dsa/circular-queue)
5. [Queue in Standard Libraries](https://docs.python.org/3/library/queue.html)

## Interview Tips
1. Clarify queue type requirements
2. Consider space/time complexity trade-offs
3. Handle edge cases explicitly
4. Use built-in implementations when allowed
5. Consider thread-safety requirements
6. Test boundary conditions thoroughly