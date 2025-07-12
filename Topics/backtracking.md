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