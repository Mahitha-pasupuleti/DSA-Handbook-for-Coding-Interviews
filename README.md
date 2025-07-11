# 📘 DSA Reference Handbook for Coding Interviews

This handbook is a curated compilation of core Data Structures and Algorithms (DSA) concepts, patterns, and resources commonly tested in coding interviews, with special emphasis on Python and Java. Each topic includes key notes, links to practice resources, and common edge cases or variations to remember.

---

## 📺 Must Watch
- [AlgoMonster Problem Solving Walkthrough (YouTube)](https://youtu.be/lvO88XxNAzs)

---

## 📚 Reference Resources
- [Python `collections` module](https://www.geeksforgeeks.org/python-collections-module/)
- [Dunder/Magic Methods in Python](https://www.geeksforgeeks.org/dunder-magic-methods-python/)
- [AlgoMonster Runtime Complexity Summary](https://algo.monster/problems/runtime_summary)
- [AlgoMonster Keyword to Algo Map](https://algo.monster/problems/keyword_to_algo)
- [bisect algorithm in Python](https://www.geeksforgeeks.org/bisect-algorithm-functions-in-python/)
- [functools.cmp_to_key in Python](https://www.geeksforgeeks.org/how-does-the-functools-cmp_to_key-function-works-in-python/)
- [UserList in Python](https://www.geeksforgeeks.org/collections-userlist-in-python/)
- [UserString in Python](https://www.geeksforgeeks.org/collections-userstring-in-python/)
- [Python Sorted Containers](https://www.geeksforgeeks.org/python-sorted-containers-an-introduction/)
- [Bit Manipulation (CP Algorithms)](https://cp-algorithms.com/algebra/bit-manipulation.html)

---

## 📌 Arrays
- **Subarray**: Contiguous block
- **Subsequence**: Can skip elements but keep the order
- **Bitonic array**: Increasing then decreasing (e.g., `[1, 3, 8, 4, 2]`)
- In C++/Java, avoid declaring large arrays inside `main()` (garbage values); prefer global declaration

---

## 🧵 Strings
- Use `Counter` from `collections` for char freq (Space is O(1))
- Efficient string search: **KMP**, **Rabin-Karp**
- KMP = Longest Prefix Suffix (LPS) table

---

## 🔃 Sorting
- **In-place**: Bubble, Selection, Insertion, Heap, Quick
- **Not In-place**: Merge
- **Python's default**: Timsort (merge + insertion)
- **Heap sort**: Best for in-place and O(n log n)
- Use `collections.defaultdict(set)` for custom hash sets

---

## 🧮 Matrix
- Create: `[[0]*cols for _ in range(rows)]`
- Copy: `[row[:] for row in matrix]`
- Transpose: `list(zip(*matrix))`

---

## 🔗 Linked List
- Java's built-in: `java.util.LinkedList`
- High insertion/deletion may affect **cache locality**

---

## ⏩ Queue
- Normal list `dequeue`: O(n)
- Use `deque.appendleft()` for O(1) left insertions

---

## 🧱 Stack
- Reverse Polish Notation = Postfix
- **Monotonic Stack**:
  - Increasing: For next smaller
  - Decreasing: For next greater

---

## 🌲 Tree
- Acyclic, undirected, connected
- Terminologies: parent, child, ancestor, descendant, depth, degree, etc.
- **BST**: Use in-order traversal for Kth smallest
- Traversals:
  - In-order, Pre-order, Post-order (recursive + iterative)
  - BFS = level-order
- Skewed binary tree: One child per node
- B-Tree search: O(log n)

---

## 🌐 Graph
- Representations: Adjacency List, Matrix, HashMap of HashMaps
- Traversals:
  - BFS (Shortest path level-wise)
  - DFS
  - Topological Sort
- **Eulerian Path/Circuit**:
  - Visits every edge once
  - Hierholzer’s Algorithm: Find Eulerian Path/Circuit

---

## 🔺 Heap / Priority Queue
- **Min Heap**: `heapq` in Python
- **Max Heap**: Use `-value` in `heapq`
- `heapify` = O(n), `push`/`pop` = O(log n)
- Use for problems like:
  - Top K elements
  - K-way merge
- Tree structure:
  - Parent: i, Children: 2i+1 and 2i+2

---

## 🔤 Trie (Prefix Tree)
- Efficient for prefix search/autocomplete
- Insert/Search/Delete: O(m), where m = length of word

---

## 📆 Interval Problems
- Clarify overlap: Is [1, 2] overlapping with [2, 3]?
- Sort intervals or use min-heap
- Often solved via line-sweep techniques

---

## 💰 Greedy
- Local optimal choice at each step
- Precondition: Greedy-choice & Optimal Substructure
- Often involves sorting

---

## 🔁 Recursion
- Time: (branches)^depth
- Space: depth of recursion stack
- Combine with memoization = DP (Top Down)

---

## 🧠 Dynamic Programming (DP)
- **Top Down (Memoization)**: Recursion + cache
- **Bottom Up (Tabulation)**: Iterative
- Use FAST framework:
  - Find naive
  - Analyze
  - Subproblem
  - Turn around to iterative

---

## 🔙 Backtracking
- Recursive brute-force + pruning
- Used when multiple valid solutions are possible (e.g., combinations, permutations)

---

## 🔄 Cyclic Sort
- For problems like:
  - Missing numbers
  - Duplicates
  - When no extra space allowed (O(1))

---

## 🧮 Bit Manipulation
| Operation | Usage Example |
|-----------|----------------|
| AND `&` | `n & (n-1)` → turn off rightmost bit |
| OR `|` | `num | (1 << i)` → set ith bit |
| XOR `^` | swap variables, check parity |
| Power of 2 | `n & (n - 1) == 0` |
| i-th bit set? | `(num >> i) & 1 != 0` |
| XOR from 1 to N | based on `N % 4` |
| Complement | `number ^ ((1 << N.bit_length()) - 1)` |

---

## ➗ Math
- **Mod for negatives**: `((n % k) + k) % k`
- Arithmetic Series: For nested loops
- Geometric Series: Perfect binary trees
- Permutations = `n! / (n - r)!`
- Combinations = `n! / [(n - r)! * r!]`
- Log scale intuition: `log(1e12) = 12`

---

## 🗺️ Hash Map / Hash Set
- O(1) average lookup
- Keys must be immutable (use `tuple`, not `list`)
- Use `collections.Counter()` for character frequency
- Collision Handling:
  - Open Addressing (Linear Probing)
  - Separate Chaining

---

## 📎 Miscellaneous
- **Catalan Number**: Useful in counting problems (e.g., number of BSTs, parenthesis combinations)
- **Constraint Estimation**:
  - 10^8 ops ≈ 1 sec
  - Choose algorithm accordingly

---

## ✅ Practice First!
- **Patterns to Master**:
  - Sliding Window
  - Two Pointers
  - Fast & Slow Pointers
  - BFS/DFS Template
  - Prefix Sum
  - Binary Search on Answer
  - Top K Elements
  - Kadane’s Algorithm
  - Union Find
  - Flood Fill
  - Graph Coloring

---

_Last updated: July 2025_

Inspired by personal prep journey and curated from trusted sources like GFG, AlgoMonster, CP-Algorithms, and FAANG mock interviews.
