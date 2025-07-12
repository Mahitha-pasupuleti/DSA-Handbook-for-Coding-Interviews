# Bit Manipulation Techniques 🧮

## Introduction
Bit manipulation involves working with individual bits in numbers. It's essential for optimizing space usage, performing fast arithmetic operations, and solving various algorithmic problems efficiently.

## Core Concepts

### Important Terminologies
- **Bit**: Binary digit (0 or 1)
- **Bitwise AND (&)**: 1 if both bits are 1
- **Bitwise OR (|)**: 1 if either bit is 1
- **Bitwise XOR (^)**: 1 if bits are different
- **Bitwise NOT (~)**: Inverts all bits
- **Left Shift (<<)**: Shifts bits left
- **Right Shift (>>)**: Shifts bits right
- **Bit Mask**: Pattern for selecting bits
- **Set Bit**: Bit with value 1
- **Clear Bit**: Bit with value 0

### Basic Operations
| Operation | Description | Example |
|-----------|-------------|---------|
| AND (&) | Both 1 | 1100 & 1010 = 1000 |
| OR (\|) | Either 1 | 1100 \| 1010 = 1110 |
| XOR (^) | Different | 1100 ^ 1010 = 0110 |
| NOT (~) | Invert | ~1100 = 0011 |
| Left Shift | Multiply by 2 | 0011 << 1 = 0110 |
| Right Shift | Divide by 2 | 0110 >> 1 = 0011 |

### Time Complexity Analysis
| Operation | Time Complexity |
|-----------|----------------|
| Basic Operations | O(1) |
| Counting Bits | O(1) or O(k)* |
| Bit Traversal | O(log n) |
| Power of 2 Check | O(1) |
| Subset Generation | O(2^n) |

*k = number of set bits (for Brian Kernighan's algorithm)

## Implementation Patterns

### 1. Basic Bit Operations
```python
def bit_operations(a: int, b: int) -> dict:
    return {
        'AND': a & b,
        'OR': a | b,
        'XOR': a ^ b,
        'NOT_A': ~a,
        'LEFT_SHIFT': a << 1,
        'RIGHT_SHIFT': a >> 1
    }

def get_bit(num: int, i: int) -> bool:
    return bool(num & (1 << i))

def set_bit(num: int, i: int) -> int:
    return num | (1 << i)

def clear_bit(num: int, i: int) -> int:
    mask = ~(1 << i)
    return num & mask

def update_bit(num: int, i: int, value: bool) -> int:
    mask = ~(1 << i)
    return (num & mask) | (value << i)
```

### 2. Counting Set Bits
```python
def count_set_bits(n: int) -> int:
    """Brian Kernighan's Algorithm"""
    count = 0
    while n:
        n &= (n - 1)  # Clear rightmost set bit
        count += 1
    return count

def count_bits_lookup(n: int) -> int:
    """Using lookup table"""
    table = [0] * 256
    for i in range(256):
        table[i] = (i & 1) + table[i >> 1]
    
    return (table[n & 0xff] +
            table[(n >> 8) & 0xff] +
            table[(n >> 16) & 0xff] +
            table[n >> 24])
```

### 3. Power of Two
```python
def is_power_of_two(n: int) -> bool:
    """Check if number is power of 2"""
    return n > 0 and (n & (n - 1)) == 0

def next_power_of_two(n: int) -> int:
    """Find next power of 2"""
    if n <= 0:
        return 1
    
    n -= 1
    n |= n >> 1
    n |= n >> 2
    n |= n >> 4
    n |= n >> 8
    n |= n >> 16
    return n + 1
```

### 4. Subset Generation
```python
def generate_subsets(nums: List[int]) -> List[List[int]]:
    n = len(nums)
    subsets = []
    
    for i in range(1 << n):  # 2^n
        subset = []
        for j in range(n):
            if i & (1 << j):
                subset.append(nums[j])
        subsets.append(subset)
    
    return subsets
```

### 5. Bit Manipulation Tricks
```python
def bit_tricks(n: int) -> dict:
    return {
        'is_even': (n & 1) == 0,
        'multiply_by_2': n << 1,
        'divide_by_2': n >> 1,
        'clear_rightmost_set_bit': n & (n - 1),
        'get_rightmost_set_bit': n & (-n),
        'clear_all_bits_except_rightmost': n & (-n),
        'clear_rightmost_bits': n & (n + 1),
        'swap_values': lambda x, y: (x := x ^ y, y := x ^ y, x := x ^ y)
    }
```

## Common Techniques

### 1. XOR Properties
```python
def xor_techniques(nums: List[int]) -> dict:
    # Properties:
    # 1. a ^ a = 0
    # 2. a ^ 0 = a
    # 3. a ^ b = b ^ a
    # 4. (a ^ b) ^ c = a ^ (b ^ c)
    
    def find_single_number():
        result = 0
        for num in nums:
            result ^= num
        return result
    
    def swap_numbers(a, b):
        a ^= b
        b ^= a
        a ^= b
        return a, b
    
    return {
        'single_number': find_single_number(),
        'swap_example': swap_numbers(5, 10)
    }
```

### 2. Bit Masking
```python
def bit_masking_examples() -> dict:
    # Create mask with n rightmost 1's
    def create_mask(n):
        return (1 << n) - 1
    
    # Clear rightmost n bits
    def clear_rightmost_bits(x, n):
        return x & (-1 << n)
    
    # Clear bits from MSB to i
    def clear_msb_to_i(x, i):
        return x & ((1 << i) - 1)
    
    return {
        'mask_3_bits': create_mask(3),          # 000...0111
        'clear_right_3': clear_rightmost_bits(0b1111, 3),  # 1000
        'clear_msb_to_2': clear_msb_to_i(0b1111, 2)       # 0011
    }
```

## Edge Cases to Consider
1. Zero input
2. Negative numbers
3. Integer overflow
4. All bits set
5. All bits clear
6. Alternating bits
7. Single bit set
8. Maximum integer
9. Minimum integer
10. Power of two values

## Common Pitfalls
1. Sign bit handling
2. Integer overflow
3. Negative shifts
4. Language-specific behavior
5. Operator precedence
6. Unsigned vs signed
7. Off-by-one errors
8. Assuming 32/64 bits

## Practice Problems by Difficulty

### Easy
1. [Single Number](https://leetcode.com/problems/single-number/) (LC #136)
2. [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) (LC #191)
3. [Power of Two](https://leetcode.com/problems/power-of-two/) (LC #231)

### Medium
1. [Single Number III](https://leetcode.com/problems/single-number-iii/) (LC #260)
2. [Counting Bits](https://leetcode.com/problems/counting-bits/) (LC #338)
3. [Subsets](https://leetcode.com/problems/subsets/) (LC #78)
4. [Reverse Bits](https://leetcode.com/problems/reverse-bits/) (LC #190)

### Hard
1. [Maximum XOR of Two Numbers in an Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/) (LC #421)
2. [Minimum Number of Flips to Convert Binary Matrix to Zero Matrix](https://leetcode.com/problems/minimum-number-of-flips-to-convert-binary-matrix-to-zero-matrix/) (LC #1284)
3. [Find XOR Sum of All Pairs Bitwise AND](https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/) (LC #1835)

## Real-World Applications
1. **Low-Level Programming**:
   - Device drivers
   - Hardware interfaces
2. **Network Programming**:
   - IP address manipulation
   - Network masks
3. **Graphics Programming**:
   - Color manipulation
   - Pixel operations
4. **Cryptography**:
   - Hash functions
   - Encryption
5. **Data Compression**:
   - Run-length encoding
   - Huffman coding
6. **Performance Optimization**:
   - Fast arithmetic
   - Memory efficiency

## Advanced Topics
1. **Advanced Bit Techniques**:
   - Gray code
   - Hamming distance
2. **Bit-Level Parallelism**:
   - SIMD operations
   - Parallel bit counting
3. **Error Detection/Correction**:
   - Parity bits
   - Hamming codes
4. **Specialized Algorithms**:
   - Population count
   - Bit reversal
5. **Hardware Aspects**:
   - CPU flags
   - Cache alignment

## Important Resources
1. [Bit Manipulation Tricks](https://graphics.stanford.edu/~seander/bithacks.html)
2. [Bit Twiddling Hacks](https://bits.stephan-brumme.com/)
3. [Advanced Bit Manipulation](https://www.geeksforgeeks.org/advanced-bit-manipulation/)
4. [Bitwise Operators in Detail](https://www.hackerearth.com/practice/basic-programming/bit-manipulation/basics-of-bit-manipulation/tutorial/)
5. [Bit Manipulation Patterns](https://leetcode.com/discuss/general-discussion/1073221/bit-manipulation-patterns)

## Interview Tips
1. Draw bit patterns
2. Test with small numbers
3. Consider edge cases
4. Use built-in functions
5. Explain bit operations
6. Consider optimization
7. Handle negative numbers
8. Test boundary conditions
9. Consider portability
10. Think about scalability