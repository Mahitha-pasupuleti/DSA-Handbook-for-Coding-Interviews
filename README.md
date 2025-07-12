# 📘 DSA Reference Handbook for Coding Interviews

This handbook is a curated and expanded guide for Data Structures and Algorithms (DSA) tailored for coding interviews at top tech companies. It includes concise definitions, edge cases, key techniques, and linked resources to help streamline your prep.

---
# 📖 List of Topics:
- [📌 Arrays](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-📌-arrays)
- [🧵 Strings](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🧵-strings)
- [🔃 Sorting](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔃-sorting)
- [🧮 Matrix](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🧮-matrix)
- [🔗 Linked List](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔗-linked-list)
- [⏩ Queue](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-⏩-queue)
- [🧱 Stack](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🧱-stack)
- [🗺️ Hash Map / Hash Set](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🗺️-hash-map--hash-set)
- [🌲 Tree](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🌲-tree)
- [🌐 Graph](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🌐-graph)
- [🔺 Heap / Priority Queue](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔺-heap--priority-queue)
- [🔤 Trie](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔤-trie)
- [📆 Intervals](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-📆-intervals)
- [💰 Greedy](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-💰-greedy)
- [🔁 Recursion](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔁-recursion)
- [🧠 Dynamic Programming](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🧠-dynamic-programming)
- [🔙 Backtracking](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔙-backtracking)
- [🔄 Cyclic Sort](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🔄-cyclic-sort)
- [🧮 Bit Manipulation](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-🧮-bit-manipulation)
- [➗ Math](https://github.com/TharunKumarReddyPolu/DSA-Handbook-for-Coding-Interviews/blob/main/README.md#topic-name-➗-math)


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
| Algorithm      | Time      | Space     | In-place | Stable |
|----------------|-----------|-----------|----------|--------|
| Bubble Sort    | O(n²)     | O(1)      | Yes      | Yes    |
| Selection Sort | O(n²)     | O(1)      | Yes      | No     |
| Insertion Sort | O(n²)     | O(1)      | Yes      | Yes    |
| Merge Sort     | O(n log n)| O(n)      | No       | Yes    |
| Quick Sort     | O(n log n)| O(log n)  | Yes     | No     |
| Heap Sort      | O(n log n)| O(1)      | Yes      | No     |

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

# Topic Name: 🗺️ Hash Map / Hash Set

### Important Terminologies:
- Hash Map: Key-value pairs with O(1) average access.
- Hash Set: Unique elements with O(1) average operations.
- Collision: When multiple keys hash to same index.

### Time Complexity:
- Insert/Access/Delete: O(1) average, O(n) worst case.

### Less Known but Important Points:
- Python uses dict and set.
- Useful for frequency counting, memoization.
- Avoid mutable keys in hash maps.

### Edge Cases to Consider:
- Duplicate keys.
- Non-existent keys.
- Mutation during iteration.

### Common Coding Interview Patterns:
- Two sum using hashmap.
- Frequency map for anagram detection.
- Caching/memoization.

### Relevant LeetCode Problems:
- [Two Sum](https://leetcode.com/problems/two-sum/) (LC #1)
- [Group Anagrams](https://leetcode.com/problems/group-anagrams/) (LC #49)
- [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) (LC #128)

### Links to Important Resources:
- [Hashing in Python](https://realpython.com/python-hash-table/)
- [Python dict](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
- [When to Use Sets vs Lists](https://stackoverflow.com/questions/2831212/python-sets-vs-lists)


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

# Topic Name: 🧠 Dynamic Programming

### Important Terminologies:
- Overlapping Subproblems: Same subproblems solved multiple times.
- Optimal Substructure: Solution to problem can be built from solutions to subproblems.
- Memoization: Top-down approach with caching.
- Tabulation: Bottom-up approach with iteration.

### Time Complexity:
- Typically O(n), O(n²), or O(n³) depending on state and transitions.

### Less Known but Important Points:
- DP problems usually involve choosing, skipping, or combining choices.
- 1D/2D arrays or hash maps commonly used for state representation.
- Identify recurrence relation early.

### Edge Cases to Consider:
- Zero input size.
- Negative numbers in state values.
- Integer overflow in recursive calls.

### Common Coding Interview Patterns:
- 0/1 Knapsack
- Longest Common Subsequence
- DP on Strings, Grids, Trees

### Relevant LeetCode Problems:
- [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) (LC #70)
- [House Robber](https://leetcode.com/problems/house-robber/) (LC #198)
- [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) (LC #5)

### Links to Important Resources:
- [DP Introduction](https://www.geeksforgeeks.org/dynamic-programming/)
- [Top-down vs Bottom-up](https://leetcode.com/discuss/general-discussion/475924/my-experience-and-thoughts-on-dynamic-programming)
- [Patterns of DP](https://www.educative.io/blog/cracking-the-coding-interview-dynamic-programming)

# Topic Name: 🔙 Backtracking

### Important Terminologies:
- Backtracking: Try out all options and undo when needed.
- State Space Tree: Tree representing all solution candidates.
- Pruning: Skip unnecessary branches early.

### Time Complexity:
- Generally exponential, O(kⁿ) or O(n!) depending on permutations/combinations.

### Less Known but Important Points:
- Often confused with DFS — but backtracking undoes choices.
- Can be combined with memoization for optimization.
- Classic tool for constraint satisfaction problems.

### Edge Cases to Consider:
- No solution case.
- Duplicates in input affecting permutations.
- Maximum depth reached early.

### Common Coding Interview Patterns:
- Subsets and permutations.
- N-Queens / Sudoku Solver.
- Word search / Path finding.

### Relevant LeetCode Problems:
- [Subsets](https://leetcode.com/problems/subsets/) (LC #78)
- [Permutations](https://leetcode.com/problems/permutations/) (LC #46)
- [N-Queens](https://leetcode.com/problems/n-queens/) (LC #51)

### Links to Important Resources:
- [Backtracking Overview](https://www.geeksforgeeks.org/backtracking-algorithms/)
- [N-Queens Explained](https://leetcode.com/problems/n-queens/solution/)
- [Backtracking Pattern](https://medium.com/@codingfreak/backtracking-is-not-recursion-73941d6f16bf)

# Topic Name: 🔄 Cyclic Sort

### Important Terminologies:
- Cyclic Sort: Sorting numbers when they are in a range 1 to n.
- In-place Swap: Swap elements without extra space.
- Index-Matching: Element value matches its index+1.

### Time Complexity:
- Best, Average, Worst: O(n)

### Less Known but Important Points:
- Does not use comparisons — uses swapping.
- Extremely space efficient.
- Detects duplicates/missing numbers efficiently.

### Edge Cases to Consider:
- Duplicate or missing elements.
- Zero or negative values (outside 1..n).
- Already sorted array.

### Common Coding Interview Patterns:
- Finding duplicates/missing numbers.
- Sorting range-limited elements.
- Place correct element at correct index.

### Relevant LeetCode Problems:
- [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) (LC #448)
- [Set Mismatch](https://leetcode.com/problems/set-mismatch/) (LC #645)
- [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)

### Links to Important Resources:
- [Cyclic Sort Pattern](https://www.educative.io/courses/grokking-coding-interview-patterns-java/qVVNDRqLZZA)
- [In-place Cyclic Sort](https://www.geeksforgeeks.org/cyclic-sort/)
- [Missing and Duplicate Pattern](https://leetcode.com/problems/find-the-duplicate-number/solution/)


# Topic Name: 🧮 Bit Manipulation

### Important Terminologies:
- XOR: Useful for finding unique elements.
- Bit Masking: Use of bits to represent sets.
- Bit Shifting: Left/right shift for power of two calculations.

### Time Complexity:
- O(1) for most operations.
- O(log n) when looping over bits.

### Less Known but Important Points:
- n & (n - 1) removes the rightmost set bit.
- XOR of same number is zero.
- Count set bits with Brian Kernighan’s algo.

### Edge Cases to Consider:
- Zero input.
- Negative numbers.
- Overflow in shifts.

### Common Coding Interview Patterns:
- Single number in pairs.
- Subset generation using bits.
- Count number of 1s.

### Relevant LeetCode Problems:
- [Single Number](https://leetcode.com/problems/single-number/) (LC #136)
- [Counting Bits](https://leetcode.com/problems/counting-bits/) (LC #338)
- [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) (LC #191)

### Links to Important Resources:
- [Bit Manipulation Tricks](https://www.geeksforgeeks.org/bitwise-hacks-for-competitive-programming/)
- [Bitwise Operators in Python](https://realpython.com/python-bitwise-operators/)
- [Bitmasking Explained](https://leetcode.com/problems/subsets/solution/)

# Topic Name: ➗ Math

### Important Terminologies:
- GCD/LCM: Greatest Common Divisor / Least Common Multiple.
- Modulo Arithmetic: Useful for large number operations.
- Prime Number: Number divisible only by 1 and itself.

### Time Complexity:
- Varies. Euclidean GCD is O(log min(a, b)).
- Sieve of Eratosthenes is O(n log log n).

### Less Known but Important Points:
- (a * b) % c = ((a % c) * (b % c)) % c
- Use fast exponentiation for power mod.
- Overflow risk with large factorials.

### Edge Cases to Consider:
- Zero and one.
- Negative numbers.
- Precision for floats.

### Common Coding Interview Patterns:
- Sieve for prime generation.
- GCD for array operations.
- Power mod / inverse mod.

### Relevant LeetCode Problems:
- [Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/) (LC #1071)
- [Count Primes](https://leetcode.com/problems/count-primes/) (LC #204)
- [Pow(x, n)](https://leetcode.com/problems/powx-n/) (LC #50)

### Links to Important Resources:
- [GCD and LCM](https://www.geeksforgeeks.org/gcd-in-python/)
- [Sieve of Eratosthenes](https://www.geeksforgeeks.org/sieve-of-eratosthenes/)
- [Modular Arithmetic](https://cp-algorithms.com/algebra/module-inverse.html)

---

## 📚 Must-Know Core References
- [Big-O Cheatsheet](https://www.bigocheatsheet.com/)
- [AlgoMonster: Runtime Complexity Summary](https://algo.monster/problems/runtime_summary)
- [AlgoMonster: Keyword to Algo](https://algo.monster/problems/keyword_to_algo)
- [Python `collections` module](https://www.geeksforgeeks.org/python-collections-module/)
- [CP Algorithms - Bit Manipulation](https://cp-algorithms.com/algebra/bit-manipulation.html)
- [Python Sorted Containers](https://www.geeksforgeeks.org/python-sorted-containers-an-introduction/)
- [Dunder Methods in Python](https://www.geeksforgeeks.org/dunder-magic-methods-python/)

---

## 📺 Best Free Video Resources
- [70 Leetcode problems in 5+ hours (every data structure) (full tutorial)](https://youtu.be/lvO88XxNAzs)
- [Neetcode 150 Youtube Playlist](https://www.youtube.com/watch?v=3OamzN90kPg&list=PLPe9IkX86X3y5m_MvtNu2ughxsvkqUNKr)

---

> Inspired by practical interview prep with insights from AlgoMonster, LeetCode, GFG, CP-Algorithms, and my personal preparation notes.

## Help me improve the project better 📈

Please discuss your concerns with [Tharun Kumar Reddy Polu](https://tharunpolu.com/) before creating a new issue/Pull Request.

_Please `STAR`⭐️ the repository if you like the content_

_Also enable the `WATCH`👁 button to keep watching the updates on the repository_


_Last updated: July 2025_
