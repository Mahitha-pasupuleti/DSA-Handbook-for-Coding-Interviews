# Hashing and Hash Tables 🗺️

## Introduction
Hashing is a technique that maps data of arbitrary size to fixed-size values. Hash tables use hashing to implement associative arrays, providing fast data access. Understanding hashing is crucial for efficient data storage and retrieval.

## Core Concepts

### Important Terminologies
- **Hash Function**: Maps data to fixed-size value
- **Hash Table**: Data structure using hash function
- **Hash Map**: Key-value pair storage
- **Hash Set**: Unique element storage
- **Collision**: Multiple keys hash to same index
- **Load Factor**: Ratio of entries to table size
- **Chaining**: Collision resolution using linked lists
- **Open Addressing**: Collision resolution by probing
- **Rehashing**: Resizing hash table
- **Bucket**: Storage unit in hash table

### Types of Hash Tables
1. **Separate Chaining**:
   - Uses linked lists for collisions
   - No size limit per bucket
   - Extra space for links

2. **Open Addressing**:
   - Linear Probing
   - Quadratic Probing
   - Double Hashing

### Time Complexity Analysis
| Operation | Average Case | Worst Case |
|-----------|--------------|------------|
| Insert    | O(1)         | O(n)       |
| Delete    | O(1)         | O(n)       |
| Search    | O(1)         | O(n)       |
| Space     | O(n)         | O(n)       |

Factors affecting performance:
- Load factor
- Hash function quality
- Collision resolution method
- Initial capacity

## Implementation Patterns

### 1. Basic Hash Map Implementation
```python
class HashMap:
    def __init__(self, size=1000):
        self.size = size
        self.table = [[] for _ in range(self.size)]
    
    def _hash(self, key):
        return hash(key) % self.size
    
    def put(self, key, value):
        hash_key = self._hash(key)
        bucket = self.table[hash_key]
        
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return
        bucket.append((key, value))
    
    def get(self, key, default=None):
        hash_key = self._hash(key)
        bucket = self.table[hash_key]
        
        for k, v in bucket:
            if k == key:
                return v
        return default
    
    def remove(self, key):
        hash_key = self._hash(key)
        bucket = self.table[hash_key]
        
        for i, (k, v) in enumerate(bucket):
            if k == key:
                del bucket[i]
                return
```

### 2. Custom Hash Function
```python
class CustomHash:
    def __init__(self):
        self.multiplier = 31
        self.modulus = 10**9 + 7
    
    def hash_string(self, s: str) -> int:
        hash_value = 0
        for char in s:
            hash_value = (hash_value * self.multiplier + ord(char)) % self.modulus
        return hash_value
    
    def hash_list(self, lst: list) -> int:
        hash_value = 0
        for item in lst:
            hash_value = (hash_value * self.multiplier + hash(item)) % self.modulus
        return hash_value
```

### 3. Rolling Hash
```python
def rolling_hash(text: str, pattern_length: int) -> List[int]:
    if not text or pattern_length <= 0:
        return []
    
    base = 26
    modulus = 10**9 + 7
    
    # Calculate the hash of first window
    window_hash = 0
    highest_power = pow(base, pattern_length - 1, modulus)
    
    for i in range(pattern_length):
        window_hash = (window_hash * base + ord(text[i])) % modulus
    
    result = [window_hash]
    
    # Calculate hash for remaining windows
    for i in range(len(text) - pattern_length):
        # Remove leading digit
        window_hash = window_hash - (ord(text[i]) * highest_power) % modulus
        if window_hash < 0:
            window_hash += modulus
        
        # Add trailing digit
        window_hash = (window_hash * base + ord(text[i + pattern_length])) % modulus
        result.append(window_hash)
    
    return result
```

### 4. Frequency Counter
```python
from collections import Counter

def frequency_analysis(items):
    # Count frequencies
    freq = Counter(items)
    
    # Find most common
    most_common = freq.most_common(3)
    
    # Find unique elements
    unique = [item for item, count in freq.items() if count == 1]
    
    # Find duplicates
    duplicates = [item for item, count in freq.items() if count > 1]
    
    return {
        'frequencies': dict(freq),
        'most_common': most_common,
        'unique': unique,
        'duplicates': duplicates
    }
```

### 5. Two Sum Pattern
```python
def two_sum(nums: List[int], target: int) -> List[int]:
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []
```

## Common Techniques

### 1. Collision Resolution
```python
class HashTableWithChaining:
    def __init__(self):
        self.size = 1000
        self.table = [[] for _ in range(self.size)]
    
    def _hash(self, key):
        return sum(ord(c) for c in str(key)) % self.size
    
    def insert(self, key, value):
        index = self._hash(key)
        chain = self.table[index]
        
        # Linear search in chain
        for i, (k, v) in enumerate(chain):
            if k == key:
                chain[i] = (key, value)
                return
        
        chain.append((key, value))
```

### 2. Load Factor Management
```python
class DynamicHashTable:
    def __init__(self, initial_size=8):
        self.size = initial_size
        self.count = 0
        self.table = [[] for _ in range(self.size)]
    
    @property
    def load_factor(self):
        return self.count / self.size
    
    def resize(self):
        if self.load_factor >= 0.75:
            old_table = self.table
            self.size *= 2
            self.table = [[] for _ in range(self.size)]
            self.count = 0
            
            for chain in old_table:
                for key, value in chain:
                    self.insert(key, value)
```

## Edge Cases to Consider
1. Empty hash table
2. Single entry
3. Multiple collisions
4. Duplicate keys
5. Non-existent keys
6. Null keys/values
7. Mutable keys
8. Integer overflow
9. High load factor
10. Concurrent access

## Common Pitfalls
1. Poor hash function
2. Not handling collisions
3. Ignoring load factor
4. Mutable key usage
5. Integer overflow
6. Memory leaks
7. Incorrect equality comparison
8. Thread safety issues

## Practice Problems by Difficulty

### Easy
1. [Two Sum](https://leetcode.com/problems/two-sum/) (LC #1)
2. [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (LC #242)
3. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (LC #217)

### Medium
1. [Group Anagrams](https://leetcode.com/problems/group-anagrams/) (LC #49)
2. [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) (LC #347)
3. [Design HashMap](https://leetcode.com/problems/design-hashmap/) (LC #706)
4. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) (LC #560)

### Hard
1. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) (LC #128)
2. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)
3. [LFU Cache](https://leetcode.com/problems/lfu-cache/) (LC #460)

## Real-World Applications
1. **Database Indexing**:
   - Fast record lookup
   - Unique key constraints
2. **Caching Systems**:
   - Memory caches
   - Web caches
3. **Cryptography**:
   - Password hashing
   - Digital signatures
4. **Data Deduplication**:
   - File systems
   - Data compression
5. **Symbol Tables**:
   - Compiler design
   - Language processing
6. **Load Balancing**:
   - Consistent hashing
   - Server selection

## Advanced Topics
1. **Perfect Hashing**:
   - Static dictionary
   - Zero collision
2. **Consistent Hashing**:
   - Distributed systems
   - Load balancing
3. **Bloom Filters**:
   - Probabilistic data structure
   - Space efficiency
4. **Cuckoo Hashing**:
   - Multiple hash functions
   - Worst-case O(1)
5. **Cryptographic Hashing**:
   - SHA family
   - MD5, bcrypt

## Important Resources
1. [Hash Table Implementation](https://www.geeksforgeeks.org/implementing-hash-table-open-addressing-linear-probing-cpp/)
2. [Collision Resolution Techniques](https://www.cs.cmu.edu/~ab/15-121N11/lectures/lecture16.pdf)
3. [Consistent Hashing](https://www.toptal.com/big-data/consistent-hashing)
4. [Perfect Hashing](https://www.geeksforgeeks.org/perfect-hashing/)
5. [Bloom Filters](https://llimllib.github.io/bloomfilter-tutorial/)

## Interview Tips
1. Choose appropriate hash function
2. Consider collision handling
3. Analyze space-time trade-offs
4. Handle edge cases
5. Consider thread safety
6. Use built-in implementations
7. Test with various inputs
8. Consider load factor
9. Discuss scalability
10. Think about security