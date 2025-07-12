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