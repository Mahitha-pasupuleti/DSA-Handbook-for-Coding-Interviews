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