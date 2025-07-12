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