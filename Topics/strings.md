# String Algorithms and Techniques 🧵

## Introduction
String manipulation and pattern matching are fundamental in computer science. Understanding string algorithms is crucial for text processing, pattern matching, and many real-world applications like text editors, compilers, and search engines.

## Core Concepts

### Important Terminologies
- **String**: Sequence of characters
- **Substring**: Contiguous sequence within string
- **Subsequence**: Characters in order (not necessarily contiguous)
- **Prefix**: Beginning part of string
- **Suffix**: Ending part of string
- **Pattern**: String to search for
- **Text**: String to search in
- **Palindrome**: Reads same forward and backward
- **Anagram**: Same characters in different order
- **Rolling Hash**: Hash that updates efficiently
- **Edit Distance**: Minimum operations to transform string

### String Properties
1. **Immutability**: Strings may be immutable (language dependent)
2. **Indexing**: Zero-based access to characters
3. **Length**: Number of characters
4. **Character Set**: ASCII, Unicode, etc.
5. **Case Sensitivity**: Upper vs lowercase

### Time Complexity Analysis
| Operation               | Average Case | Worst Case |
|------------------------|--------------|------------|
| Access                 | O(1)         | O(1)       |
| Search                 | O(n)         | O(n)       |
| Insert/Delete         | O(n)         | O(n)       |
| Concatenate           | O(n+m)       | O(n+m)     |
| Pattern Match (Naive) | O(nm)        | O(nm)      |
| Pattern Match (KMP)   | O(n+m)       | O(n+m)     |
| Rabin-Karp           | O(n+m)       | O(nm)      |

Where:
- n = length of text
- m = length of pattern

## Implementation Patterns

### 1. String Matching (KMP Algorithm)
```python
def compute_lps(pattern):
    m = len(pattern)
    lps = [0] * m
    length = 0
    i = 1
    
    while i < m:
        if pattern[i] == pattern[length]:
            length += 1
            lps[i] = length
            i += 1
        else:
            if length != 0:
                length = lps[length - 1]
            else:
                lps[i] = 0
                i += 1
    return lps

def kmp_search(text, pattern):
    n, m = len(text), len(pattern)
    lps = compute_lps(pattern)
    
    i = j = 0
    indices = []
    
    while i < n:
        if pattern[j] == text[i]:
            i += 1
            j += 1
        
        if j == m:
            indices.append(i - j)
            j = lps[j - 1]
        elif i < n and pattern[j] != text[i]:
            if j != 0:
                j = lps[j - 1]
            else:
                i += 1
    
    return indices
```

### 2. Rabin-Karp Algorithm
```python
def rabin_karp(text, pattern):
    n, m = len(text), len(pattern)
    if m > n:
        return []
    
    # Prime number for hash
    prime = 101
    # Number of characters in input alphabet
    d = 256
    
    # Calculate pattern hash
    pattern_hash = 0
    window_hash = 0
    h = pow(d, m-1) % prime
    
    # Calculate initial hash values
    for i in range(m):
        pattern_hash = (d * pattern_hash + ord(pattern[i])) % prime
        window_hash = (d * window_hash + ord(text[i])) % prime
    
    result = []
    
    # Slide pattern over text
    for i in range(n - m + 1):
        if pattern_hash == window_hash:
            if text[i:i+m] == pattern:
                result.append(i)
        
        if i < n - m:
            window_hash = (d * (window_hash - ord(text[i]) * h) + 
                         ord(text[i + m])) % prime
            if window_hash < 0:
                window_hash += prime
    
    return result
```

### 3. Palindrome Check
```python
def is_palindrome(s: str) -> bool:
    # Remove non-alphanumeric and convert to lowercase
    s = ''.join(c.lower() for c in s if c.isalnum())
    return s == s[::-1]

def longest_palindrome_substring(s: str) -> str:
    if not s:
        return ""
    
    def expand_around_center(left: int, right: int) -> int:
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return right - left - 1
    
    start = end = 0
    for i in range(len(s)):
        len1 = expand_around_center(i, i)
        len2 = expand_around_center(i, i + 1)
        length = max(len1, len2)
        if length > end - start:
            start = i - (length - 1) // 2
            end = i + length // 2
    
    return s[start:end + 1]
```

### 4. Anagram Detection
```python
from collections import Counter

def are_anagrams(s1: str, s2: str) -> bool:
    return Counter(s1) == Counter(s2)

def find_all_anagrams(s: str, p: str) -> List[int]:
    result = []
    p_count = Counter(p)
    window_count = Counter()
    
    for i in range(len(s)):
        # Add new character
        window_count[s[i]] += 1
        
        # Remove character from window if window size > pattern
        if i >= len(p):
            window_count[s[i - len(p)]] -= 1
            if window_count[s[i - len(p)]] == 0:
                del window_count[s[i - len(p)]]
        
        # Check if current window is anagram
        if window_count == p_count:
            result.append(i - len(p) + 1)
    
    return result
```

### 5. String Compression
```python
def compress(chars: List[str]) -> int:
    write = anchor = 0
    for read, char in enumerate(chars):
        if read + 1 == len(chars) or chars[read + 1] != char:
            chars[write] = chars[anchor]
            write += 1
            
            if read > anchor:
                count = read - anchor + 1
                for digit in str(count):
                    chars[write] = digit
                    write += 1
            
            anchor = read + 1
    
    return write
```

## Common Techniques

### 1. Sliding Window
```python
def longest_substring_without_repeating(s: str) -> int:
    char_index = {}
    max_length = start = 0
    
    for i, char in enumerate(s):
        if char in char_index and char_index[char] >= start:
            start = char_index[char] + 1
        else:
            max_length = max(max_length, i - start + 1)
        char_index[char] = i
    
    return max_length
```

### 2. Two Pointers
```python
def reverse_string(s: List[str]) -> None:
    left, right = 0, len(s) - 1
    while left < right:
        s[left], s[right] = s[right], s[left]
        left += 1
        right -= 1
```

## Edge Cases to Consider
1. Empty string
2. Single character string
3. All same characters
4. Special characters
5. Unicode characters
6. Whitespace
7. Case sensitivity
8. Very long strings
9. Pattern longer than text
10. Overlapping patterns

## Common Pitfalls
1. Not handling empty strings
2. Incorrect case handling
3. Buffer overflow
4. Unicode issues
5. Inefficient concatenation
6. Memory leaks
7. Off-by-one errors
8. Incorrect boundary checks

## Practice Problems by Difficulty

### Easy
1. [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (LC #242)
2. [Reverse String](https://leetcode.com/problems/reverse-string/) (LC #344)
3. [First Unique Character](https://leetcode.com/problems/first-unique-character-in-a-string/) (LC #387)

### Medium
1. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) (LC #3)
2. [Group Anagrams](https://leetcode.com/problems/group-anagrams/) (LC #49)
3. [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) (LC #5)
4. [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/) (LC #8)

### Hard
1. [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/) (LC #10)
2. [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) (LC #76)
3. [Text Justification](https://leetcode.com/problems/text-justification/) (LC #68)

## Real-World Applications
1. **Text Editors**:
   - Search and replace
   - Syntax highlighting
2. **Compilers**:
   - Lexical analysis
   - Pattern matching
3. **Search Engines**:
   - Pattern matching
   - Relevance ranking
4. **Bioinformatics**:
   - DNA sequence matching
   - Protein analysis
5. **Data Validation**:
   - Input sanitization
   - Format checking
6. **Natural Language Processing**:
   - Text analysis
   - Language detection

## Advanced Topics
1. **String Matching Algorithms**:
   - Boyer-Moore
   - Aho-Corasick
2. **Suffix Arrays/Trees**:
   - Construction
   - Applications
3. **Regular Expressions**:
   - Pattern compilation
   - Efficient matching
4. **Unicode Handling**:
   - Normalization
   - Collation
5. **String Distance Metrics**:
   - Levenshtein
   - Hamming

## Important Resources
1. [String Algorithms](https://www.geeksforgeeks.org/string-algorithms/)
2. [KMP Algorithm](https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/)
3. [Rabin-Karp Algorithm](https://www.geeksforgeeks.org/rabin-karp-algorithm-for-pattern-searching/)
4. [String Matching Patterns](https://www.cs.princeton.edu/~rs/AlgsDS07/21PatternMatching.pdf)
5. [Unicode Standards](https://www.unicode.org/standard/standard.html)

## Interview Tips
1. Clarify string properties
2. Consider case sensitivity
3. Handle special characters
4. Check for constraints
5. Consider space optimization
6. Use built-in functions wisely
7. Test with edge cases
8. Consider performance
9. Handle invalid input
10. Think about scalability