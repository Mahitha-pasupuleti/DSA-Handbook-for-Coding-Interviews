# Topic Name: ⏩ Queue

### Important Terminologies:
- Queue: FIFO data structure.
- Deque: Double-ended queue with O(1) insertions/removals at both ends.
- Circular Queue: Queue implemented in circular manner.

### Time Complexity:
- Enqueue: O(1)
- Dequeue: O(1)
- Peek: O(1)

### Less Known but Important Points:
- Python’s collections.deque is highly optimized.
- Use queue for BFS traversal.
- Sliding window max uses deque for optimization.

### Edge Cases to Consider:
- Empty queue.
- Single element.
- Overflow in fixed size queue.

### Common Coding Interview Patterns:
- BFS traversal.
- Sliding window maximum.
- Design Circular Queue.

### Relevant LeetCode Problems:
- [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) (LC #232)
- [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/) (LC #239)
- [Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC #200)

### Links to Important Resources:
- [Python deque](https://docs.python.org/3/library/collections.html#collections.deque)
- [Queue in Java](https://www.geeksforgeeks.org/queue-interface-java/)
- [Circular Queue Explanation](https://www.geeksforgeeks.org/circular-queue-set-1-introduction-array-implementation/)