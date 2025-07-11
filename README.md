# 📘 DSA Reference Handbook for Coding Interviews

This handbook is a curated and expanded guide for Data Structures and Algorithms (DSA) tailored for coding interviews at top tech companies. It includes concise definitions, edge cases, key techniques, and linked resources to help streamline your prep.

---

## 📺 Watch This First
- [AlgoMonster Deep Dive (YouTube)](https://youtu.be/lvO88XxNAzs)

---

## 📚 Core Resources
- [Python `collections` module](https://www.geeksforgeeks.org/python-collections-module/)
- [Dunder Methods in Python](https://www.geeksforgeeks.org/dunder-magic-methods-python/)
- [AlgoMonster: Runtime Complexity Summary](https://algo.monster/problems/runtime_summary)
- [AlgoMonster: Keyword to Algo](https://algo.monster/problems/keyword_to_algo)
- [CP Algorithms - Bit Manipulation](https://cp-algorithms.com/algebra/bit-manipulation.html)
- [Python Sorted Containers](https://www.geeksforgeeks.org/python-sorted-containers-an-introduction/)

---

# Topic Name: 📌 Arrays

### Important Terminologies:
- Subarray: Contiguous elements within an array.
- Subsequence: Non-contiguous elements maintaining relative order.
- Bitonic Array: Array which first increases then decreases.

### Time Complexity:
- Best case: O(n)
- Average case: O(n)
- Worst case: O(n)

### Less Known but Important Points:
- Arrays have cache locality advantages over linked lists.
- Sliding window technique is optimal for many subarray problems.
- Prefix sums help optimize range queries.

### Edge Cases to Consider:
- Empty array.
- All negative values (especially for max subarray).
- Arrays with duplicates.

### Common Coding Interview Patterns:
- Sliding Window
- Two Pointer
- Prefix Sum

### Relevant LeetCode Problems:
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) (LC #53)
- [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/) (LC #438)
- [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) (LC #11)

### Links to Important Resources:
- [Python bisect](https://www.geeksforgeeks.org/bisect-algorithm-functions-in-python/)
- [Sliding Window Technique](https://leetcode.com/problems/minimum-size-subarray-sum/solution/)
- [Prefix Sum Array](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/)


# Topic Name: 🧵 Strings

### Important Terminologies:
- Fixed-size Hash: Constant time hash for limited charset.
- KMP (Knuth-Morris-Pratt): Efficient pattern search algorithm.
- Rabin-Karp: Rolling hash pattern matching.

### Time Complexity:
- Best case: O(n)
- Average case: O(n)
- Worst case: O(n*m) (naive), O(n) (with KMP/Rabin-Karp)

### Less Known but Important Points:
- Case sensitivity impacts string matching.
- Special characters and whitespace need careful handling.
- Rolling hash reduces recomputation in pattern matching.

### Edge Cases to Consider:
- Empty string.
- Strings with special or whitespace characters.
- Case sensitivity differences.

### Common Coding Interview Patterns:
- Anagram checking
- Palindrome detection
- Longest substring without repeating characters

### Relevant LeetCode Problems:
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) (LC #3)
- [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (LC #242)
- [Implement strStr()](https://leetcode.com/problems/implement-strstr/) (LC #28)

### Links to Important Resources:
- [KMP Algorithm](https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/)
- [Rabin-Karp Algorithm](https://www.geeksforgeeks.org/rabin-karp-algorithm-for-pattern-searching/)
- [Python Counter Usage](https://docs.python.org/3/library/collections.html#collections.Counter)


# Topic Name: 🔃 Sorting

### Important Terminologies:
- In-place: Sorting done without extra space.
- Stable: Equal elements maintain order.
- Timsort: Hybrid sorting algorithm used in Python.

### Time Complexity:
| Algorithm      | Best Case  | Average Case | Worst Case  |
|----------------|------------|--------------|-------------|
| Bubble Sort    | O(n)       | O(n²)        | O(n²)       |
| Quick Sort     | O(n log n) | O(n log n)   | O(n²)       |
| Merge Sort     | O(n log n) | O(n log n)   | O(n log n)  |

### Less Known but Important Points:
- Quick Sort’s worst case can be avoided with random pivot.
- Merge Sort requires extra space but is stable.
- Python’s sort uses Timsort, efficient for partially sorted data.

### Edge Cases to Consider:
- Large inputs.
- Arrays with many duplicates.
- Already sorted arrays.

### Common Coding Interview Patterns:
- Partitioning (Quick Sort)
- Merge operation (Merge Sort)
- Counting inversions

### Relevant LeetCode Problems:
- [Sort Colors](https://leetcode.com/problems/sort-colors/) (LC #75)
- [Merge Intervals](https://leetcode.com/problems/merge-intervals/) (LC #56)
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) (LC #215)

### Links to Important Resources:
- [Sorting Algorithms Overview](https://www.geeksforgeeks.org/sorting-algorithms/)
- [Timsort Explained](https://www.geeksforgeeks.org/timsort/)
- [Quick Sort Implementation](https://www.geeksforgeeks.org/quick-sort/)


# Topic Name: 🧮 Matrix

### Important Terminologies:
- Transpose: Flipping matrix over its diagonal.
- Zero Matrix: Matrix initialized with zeros.
- Spiral Order: Traversing matrix in spiral pattern.

### Time Complexity:
- Typically O(rows * cols) for traversal or transformation.

### Less Known but Important Points:
- Use zip(*matrix) for transpose in Python.
- DFS and BFS useful for flood fill.
- In-place rotation is tricky but optimal.

### Edge Cases to Consider:
- Empty matrix.
- Single row or single column.
- Square vs rectangular matrices.

### Common Coding Interview Patterns:
- Matrix rotation
- Flood fill
- Spiral order traversal

### Relevant LeetCode Problems:
- [Rotate Image](https://leetcode.com/problems/rotate-image/) (LC #48)
- [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) (LC #54)
- [Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC #200)

### Links to Important Resources:
- [Matrix Transpose in Python](https://stackoverflow.com/questions/8421337/transpose-list-of-lists-in-python)
- [Flood Fill Algorithm](https://leetcode.com/problems/flood-fill/)
- [Spiral Matrix Explanation](https://www.geeksforgeeks.org/print-matrix-in-spiral-form/)


# Topic Name: 🔗 Linked List

### Important Terminologies:
- Singly Linked List: Nodes with single pointer.
- Doubly Linked List: Nodes with next and prev pointers.
- Circular Linked List: Last node points to first node.

### Time Complexity:
- Traversal: O(n)
- Insertion/Deletion at head: O(1)
- Searching: O(n)

### Less Known but Important Points:
- Use dummy nodes to simplify edge cases.
- Linked lists have poor cache locality compared to arrays.
- Detect cycles using Floyd’s Tortoise and Hare.

### Edge Cases to Consider:
- Empty list.
- Single node list.
- Cycle presence.

### Common Coding Interview Patterns:
- Two pointers (fast and slow).
- Reverse linked list.
- Merge k sorted lists (using heap).

### Relevant LeetCode Problems:
- [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (LC #206)
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) (LC #141)
- [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC #23)

### Links to Important Resources:
- [Floyd’s Cycle Detection](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)
- [Linked List Introduction](https://www.geeksforgeeks.org/data-structures/linked-list/)
- [Dummy Node Usage](https://leetcode.com/problems/remove-nth-node-from-end-of-list/solution/)


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


# Topic Name: 🧱 Stack

### Important Terminologies:
- Stack: LIFO data structure.
- MinStack: Stack supporting O(1) getMin.
- Monotonic Stack: Stack maintaining increasing or decreasing order.

### Time Complexity:
- Push: O(1)
- Pop: O(1)
- Peek: O(1)

### Less Known but Important Points:
- Evaluate expressions using stack (RPN).
- Parentheses matching is a classic stack problem.
- Monotonic stacks solve Next Greater/Smaller element.

### Edge Cases to Consider:
- Stack underflow.
- Empty input.
- Nested parentheses.

### Common Coding Interview Patterns:
- Parentheses matching.
- Evaluate Reverse Polish Notation.
- Next Greater Element.

### Relevant LeetCode Problems:
- [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) (LC #20)
- [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) (LC #150)
- [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) (LC #496)

### Links to Important Resources:
- [Stack Introduction](https://www.geeksforgeeks.org/stack-data-structure/)
- [Monotonic Stack Pattern](https://leetcode.com/problems/daily-temperatures/solution/)
- [MinStack Implementation](https://leetcode.com/problems/min-stack/solution/)


# Topic Name: 🌲 Tree

### Important Terminologies:
- Inorder Traversal: Left, Root, Right.
- Preorder Traversal: Root, Left, Right.
- Postorder Traversal: Left, Right, Root.
- Level Order Traversal: BFS on tree.

### Time Complexity:
- Traversal: O(n)

### Less Known but Important Points:
- Skewed trees behave like linked lists.
- Height vs Depth difference.
- Lowest Common Ancestor important for many problems.

### Edge Cases to Consider:
- Empty tree.
- Single node tree.
- Skewed (left or right) trees.

### Common Coding Interview Patterns:
- DFS traversals.
- Binary Search Tree (BST) properties.
- Path sum problems.

### Relevant LeetCode Problems:
- [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/) (LC #94)
- [Lowest Common Ancestor of a BST](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) (LC #235)
- [Path Sum](https://leetcode.com/problems/path-sum/) (LC #112)

### Links to Important Resources:
- [Tree Traversals](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)
- [LCA Explanation](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/solution/)
- [Binary Tree Path Sum](https://leetcode.com/problems/path-sum/solution/)


# Topic Name: 🌐 Graph

### Important Terminologies:
- Adjacency List: Graph representation using lists.
- Directed Acyclic Graph (DAG): Graph with no cycles.
- Union-Find: Data structure for cycle detection.

### Time Complexity:
- BFS/DFS traversal: O(V + E)

### Less Known but Important Points:
- Use adjacency list for sparse graphs.
- Topological sort on DAG.
- Cycle detection differs for directed/undirected graphs.

### Edge Cases to Consider:
- Disconnected graph.
- Graph with cycles.
- Self-loops.

### Common Coding Interview Patterns:
- BFS shortest path.
- DFS backtracking.
- Topological sort.

### Relevant LeetCode Problems:
- [Course Schedule](https://leetcode.com/problems/course-schedule/) (LC #207)
- [Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC #200)
- [Clone Graph](https://leetcode.com/problems/clone-graph/) (LC #133)

### Links to Important Resources:
- [Graph Representation](https://www.geeksforgeeks.org/graph-and-its-representations/)
- [Topological Sort](https://www.geeksforgeeks.org/topological-sorting/)
- [Union-Find Algorithm](https://www.geeksforgeeks.org/union-find/)


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


# Topic Name: 🔤 Trie

### Important Terminologies:
- Trie Node: Each node stores children and end-of-word flag.
- Prefix Search: Finding words starting with given prefix.
- Autocomplete: Suggesting words from prefixes.

### Time Complexity:
- Insert/Search/Delete: O(m) where m = length of word.

### Less Known but Important Points:
- Memory intensive compared to hash maps.
- Useful for dictionary and autocomplete applications.
- Can be implemented using arrays or hash maps.

### Edge Cases to Consider:
- Empty string insertion.
- Prefix is entire word.
- Overlapping prefixes.

### Common Coding Interview Patterns:
- Word dictionary implementation.
- Replace words in sentence.
- Prefix matching.

### Relevant LeetCode Problems:
- [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/) (LC #208)
- [Add and Search Word](https://leetcode.com/problems/add-and-search-word-data-structure-design/) (LC #211)
- [Replace Words](https://leetcode.com/problems/replace-words/) (LC #648)

### Links to Important Resources:
- [Trie Introduction](https://www.geeksforgeeks.org/trie-insert-and-search/)
- [Trie Applications](https://www.programiz.com/dsa/trie)
- [Trie vs Hash Map](https://www.geeksforgeeks.org/trie-vs-hashmap/)


# Topic Name: 📆 Intervals

### Important Terminologies:
- Interval: Range defined by start and end.
- Overlapping intervals: Intervals that intersect.
- Merge intervals: Combine overlapping intervals.

### Time Complexity:
- Sorting intervals: O(n log n)
- Merging: O(n)

### Less Known but Important Points:
- Clarify whether touching intervals count as overlapping.
- Use heaps for meeting room problems.
- Nested intervals require careful handling.

### Edge Cases to Consider:
- Single interval.
- Fully nested intervals.
- Intervals with same start or end.

### Common Coding Interview Patterns:
- Merge intervals.
- Meeting rooms.
- Interval scheduling.

### Relevant LeetCode Problems:
- [Merge Intervals](https://leetcode.com/problems/merge-intervals/) (LC #56)
- [Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/) (LC #253)
- [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/) (LC #435)

### Links to Important Resources:
- [Interval Scheduling](https://www.geeksforgeeks.org/interval-scheduling/)
- [Heap for Intervals](https://leetcode.com/problems/meeting-rooms-ii/solution/)
- [Merge Intervals Explained](https://www.programiz.com/dsa/merge-intervals)


# Topic Name: 💰 Greedy

### Important Terminologies:
- Greedy Choice Property: Locally optimal choice leads to global optimum.
- Optimal Substructure: Problem can be solved by optimal solutions to subproblems.

### Time Complexity:
- Generally O(n log n) due to sorting.

### Less Known but Important Points:
- Greedy does not always guarantee optimal solution.
- Often used in interval and scheduling problems.
- Useful for Huffman coding and coin change (limited cases).

### Edge Cases to Consider:
- Input order sensitivity.
- Equal weights/values.
- Edge cases violating greedy property.

### Common Coding Interview Patterns:
- Activity selection.
- Interval partitioning.
- Huffman encoding.

### Relevant LeetCode Problems:
- [Partition Labels](https://leetcode.com/problems/partition-labels/) (LC #763)
- [Assign Cookies](https://leetcode.com/problems/assign-cookies/) (LC #455)
- [Jump Game](https://leetcode.com/problems/jump-game/) (LC #55)

### Links to Important Resources:
- [Greedy Algorithms](https://www.geeksforgeeks.org/greedy-algorithms/)
- [Activity Selection Problem](https://www.geeksforgeeks.org/activity-selection-problem-greedy-algo-1/)
- [Huffman Coding](https://www.geeksforgeeks.org/huffman-coding-greedy-algo-3/)


# Topic Name: 🔁 Recursion

### Important Terminologies:
- Base Case: Condition to stop recursion.
- Recursive Call: Function calling itself.
- Recursive Tree: Visualization of recursive calls.

### Time Complexity:
- Depends on recursion depth and branching.

### Less Known but Important Points:
- Avoid stack overflow with base cases.
- Memoization reduces repeated calls.
- Tail recursion optimization not supported in Python.

### Edge Cases to Consider:
- Missing base case.
- Deep recursion stack.
- Input that causes exponential calls.

### Common Coding Interview Patterns:
- Divide and conquer.
- Backtracking.
- Tree

_Last updated: July 2025_

> Inspired by practical interview prep with insights from AlgoMonster, LeetCode, GFG, CP-Algorithms, and personal notes.
