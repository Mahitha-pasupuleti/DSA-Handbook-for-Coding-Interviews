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