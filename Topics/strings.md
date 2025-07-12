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