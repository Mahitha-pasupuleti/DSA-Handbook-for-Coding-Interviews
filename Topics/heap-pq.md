# Topic Name: 🔺 Heap / Priority Queue

### Important Terminologies:
- Min Heap: Smallest element at root.
- Max Heap: Largest element at root.
- Heapify: Process of building a heap.

### Time Complexity:
- Insert: O(log n)
- Extract Min/Max: O(log n)
- Peek: O(1)

### Less Known but Important Points:
- Python’s `heapq` is min-heap by default.
- Use negative values for max-heap behavior.
- Parent and child index formulas.

### Edge Cases to Consider:
- Empty heap.
- Duplicates.
- All elements equal.

### Common Coding Interview Patterns:
- Top K elements.
- Median in a stream.
- Merge k sorted lists.

### Relevant LeetCode Problems:
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) (LC #215)
- [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC #23)
- [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) (LC #295)

### Links to Important Resources:
- [Heapq Documentation](https://docs.python.org/3/library/heapq.html)
- [Heap Operations](https://www.geeksforgeeks.org/heap-data-structure/)
- [Priority Queue in Python](https://realpython.com/python-priority-queues/)