# Trie (Prefix Tree) Data Structure 🔤

## Introduction
A trie (pronounced "try") is a tree-like data structure used to store and retrieve strings. It's particularly efficient for prefix-based operations and is commonly used in applications like autocomplete, spell checkers, and IP routing tables.

## Core Concepts

### Important Terminologies
- **Trie**: Tree-like data structure for storing strings
- **Node**: Contains children references and flags
- **Root**: Starting node of the trie
- **Prefix**: Common starting characters of strings
- **Terminal Node**: Marks end of a complete word
- **Children**: Next characters in sequences
- **Branch**: Path from root to any node
- **Leaf**: Node with no children
- **Pattern**: Sequence of characters to match

### Time Complexity Analysis
| Operation          | Average Case | Worst Case |
|-------------------|--------------|------------|
| Insert            | O(m)         | O(m)       |
| Search            | O(m)         | O(m)       |
| Delete            | O(m)         | O(m)       |
| Prefix Search     | O(p + n)     | O(p + n)   |
| Space Complexity  | O(ALPHABET_SIZE * m * n) | O(ALPHABET_SIZE * m * n) |

Where:
- m = length of word
- p = length of prefix
- n = number of matches
- ALPHABET_SIZE = size of character set

## Implementation

### Basic Trie Node
```python
class TrieNode:
    def __init__(self):
        self.children = {}  # or [None] * ALPHABET_SIZE
        self.is_end_of_word = False
```

### Complete Trie Implementation
```python
class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True
    
    def search(self, word: str) -> bool:
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end_of_word
    
    def starts_with(self, prefix: str) -> bool:
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
    
    def get_words_with_prefix(self, prefix: str) -> List[str]:
        words = []
        node = self.root
        
        # Traverse to prefix node
        for char in prefix:
            if char not in node.children:
                return words
            node = node.children[char]
        
        # DFS to find all words
        def dfs(node, curr_word):
            if node.is_end_of_word:
                words.append(curr_word)
            
            for char, child in node.children.items():
                dfs(child, curr_word + char)
        
        dfs(node, prefix)
        return words
```

## Common Applications

### 1. Autocomplete System
```python
class AutocompleteSystem:
    def __init__(self, words: List[str], times: List[int]):
        self.trie = Trie()
        self.word_count = {}
        for word, count in zip(words, times):
            self.word_count[word] = count
            self.trie.insert(word)
    
    def input(self, c: str) -> List[str]:
        if c == '#':
            # Complete current word
            return []
        
        # Get suggestions
        suggestions = self.trie.get_words_with_prefix(c)
        # Sort by frequency and lexicographically
        suggestions.sort(key=lambda x: (-self.word_count.get(x, 0), x))
        return suggestions[:3]  # Return top 3
```

### 2. Spell Checker
```python
class SpellChecker:
    def __init__(self, dictionary: List[str]):
        self.trie = Trie()
        for word in dictionary:
            self.trie.insert(word)
    
    def suggest_corrections(self, word: str) -> List[str]:
        suggestions = []
        
        def dfs(node, curr_word, edits):
            if edits > 1:  # Allow max 1 edit
                return
            
            if node.is_end_of_word and edits <= 1:
                suggestions.append(curr_word)
            
            for char in 'abcdefghijklmnopqrstuvwxyz':
                if char in node.children:
                    # No edit
                    dfs(node.children[char], curr_word + char, edits)
                else:
                    # Try with edit
                    dfs(node.children.get(char, TrieNode()), 
                        curr_word + char, edits + 1)
        
        dfs(self.trie.root, "", 0)
        return suggestions
```

## Common Patterns

### 1. Word Dictionary with Wildcards
```python
def search_with_dots(self, word: str) -> bool:
    def dfs(node, word, index):
        if index == len(word):
            return node.is_end_of_word
        
        if word[index] == '.':
            for child in node.children.values():
                if dfs(child, word, index + 1):
                    return True
            return False
        
        if word[index] not in node.children:
            return False
        
        return dfs(node.children[word[index]], word, index + 1)
    
    return dfs(self.root, word, 0)
```

### 2. Replace Words with Roots
```python
def replace_with_root(self, sentence: str, roots: List[str]) -> str:
    # Build trie with roots
    trie = Trie()
    for root in roots:
        trie.insert(root)
    
    words = sentence.split()
    for i, word in enumerate(words):
        node = trie.root
        for j, char in enumerate(word):
            if char not in node.children:
                break
            node = node.children[char]
            if node.is_end_of_word:
                words[i] = word[:j+1]
                break
    
    return ' '.join(words)
```

## Edge Cases to Consider
1. Empty string operations
2. Single character words
3. Overlapping prefixes
4. Case sensitivity
5. Special characters
6. Very long words
7. Words that are prefixes of other words
8. Maximum word length
9. Memory constraints
10. Concurrent access

## Common Pitfalls
1. Not handling memory efficiently
2. Incorrect end-of-word marking
3. Case sensitivity issues
4. Not cleaning up deleted words
5. Inefficient children implementation
6. Not considering space complexity
7. Poor handling of special characters

## Practice Problems by Difficulty

### Easy
1. [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/) (LC #208)
2. [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/) (LC #14)
3. [Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/) (LC #677)

### Medium
1. [Add and Search Word](https://leetcode.com/problems/add-and-search-word-data-structure-design/) (LC #211)
2. [Replace Words](https://leetcode.com/problems/replace-words/) (LC #648)
3. [Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system/) (LC #642)
4. [Word Search II](https://leetcode.com/problems/word-search-ii/) (LC #212)

### Hard
1. [Stream of Characters](https://leetcode.com/problems/stream-of-characters/) (LC #1032)
2. [Word Squares](https://leetcode.com/problems/word-squares/) (LC #425)
3. [Palindrome Pairs](https://leetcode.com/problems/palindrome-pairs/) (LC #336)

## Real-World Applications
1. **Autocomplete Systems**: Search suggestions
2. **Spell Checkers**: Word validation and correction
3. **IP Routing Tables**: Network routing
4. **Phone Directories**: Contact search
5. **Text Editors**: Word completion
6. **DNA Analysis**: Pattern matching
7. **Natural Language Processing**: Word prediction

## Advanced Topics
1. **Compressed Trie (Radix Tree)**:
   - Path compression
   - Space optimization
2. **Ternary Search Tree**:
   - Space-efficient alternative
3. **Suffix Tree/Array**:
   - Pattern matching
   - String operations
4. **Patricia Trie**:
   - Compact representation
5. **Concurrent Trie**:
   - Thread-safe operations

## Important Resources
1. [Trie Data Structure](https://www.geeksforgeeks.org/trie-insert-and-search/)
2. [Advanced Trie Concepts](https://www.toptal.com/java/the-trie-a-neglected-data-structure)
3. [Compressed Trie Tutorial](https://www.geeksforgeeks.org/pattern-searching-using-compressed-trie/)
4. [Suffix Tree Applications](https://www.geeksforgeeks.org/pattern-searching-using-suffix-tree/)
5. [Trie vs Hash Table](https://www.geeksforgeeks.org/advantages-trie-data-structure/)

## Interview Tips
1. Clarify character set and constraints
2. Consider memory-space tradeoffs
3. Discuss optimization possibilities
4. Handle edge cases explicitly
5. Consider case sensitivity
6. Implement helper functions
7. Test with small examples
8. Consider deletion requirements