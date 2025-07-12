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