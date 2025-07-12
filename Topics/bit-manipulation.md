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