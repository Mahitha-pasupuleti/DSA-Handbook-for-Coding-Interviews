# Cyclic Sort Algorithm 🔄

## Introduction
Cyclic Sort is a pattern used to solve array problems where the array contains numbers in a given range. It's particularly efficient for problems involving arrays containing numbers from 1 to n, as it sorts the array in O(n) time without using extra space.

## Core Concepts

### Important Terminologies
- **Cyclic Sort**: Algorithm for sorting numbers in range 1 to n
- **In-place Swap**: Exchange elements without extra space
- **Index Matching**: Element value equals index + 1
- **Range Constraint**: Numbers limited to specific range
- **Missing Number**: Value absent from sequence
- **Duplicate Number**: Value appearing multiple times
- **Corruption**: When array violates range property
- **Natural Number**: Positive integers (1 to n)
- **Zero-based**: Array indices start from 0
- **One-based**: Numbers start from 1

### Properties of Cyclic Sort
1. **Time Efficiency**: O(n) for all cases
2. **Space Efficiency**: O(1) extra space
3. **Stability**: Not stable
4. **In-Place**: Yes
5. **Adaptive**: No
6. **Comparison-Based**: No

### Time Complexity Analysis
| Operation           | Time Complexity | Space Complexity |
|--------------------|----------------|------------------|
| Sorting            | O(n)           | O(1)             |
| Finding Duplicate  | O(n)           | O(1)             |
| Finding Missing    | O(n)           | O(1)             |
| Finding Multiple   | O(n)           | O(1)             |
| Corruption Check   | O(n)           | O(1)             |

## Implementation Patterns

### 1. Basic Cyclic Sort
```python
def cyclic_sort(nums):
    i = 0
    while i < len(nums):
        correct_pos = nums[i] - 1
        if nums[i] > 0 and nums[i] <= len(nums) and nums[i] != nums[correct_pos]:
            nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
        else:
            i += 1
    return nums
```

### 2. Find Missing Number
```python
def find_missing_number(nums):
    i = 0
    while i < len(nums):
        correct_pos = nums[i]
        if nums[i] < len(nums) and nums[i] != nums[correct_pos]:
            nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
        else:
            i += 1
    
    # Find the missing number
    for i in range(len(nums)):
        if nums[i] != i:
            return i
    
    return len(nums)
```

### 3. Find Duplicate Number
```python
def find_duplicate(nums):
    i = 0
    while i < len(nums):
        if nums[i] != i + 1:
            correct_pos = nums[i] - 1
            if nums[i] != nums[correct_pos]:
                nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
            else:
                return nums[i]
        else:
            i += 1
    return -1
```

### 4. Find All Missing Numbers
```python
def find_missing_numbers(nums):
    i = 0
    while i < len(nums):
        correct_pos = nums[i] - 1
        if nums[i] != nums[correct_pos]:
            nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
        else:
            i += 1
    
    missing_numbers = []
    for i in range(len(nums)):
        if nums[i] != i + 1:
            missing_numbers.append(i + 1)
    
    return missing_numbers
```

### 5. Find First Missing Positive
```python
def first_missing_positive(nums):
    i = 0
    while i < len(nums):
        correct_pos = nums[i] - 1
        if 0 < nums[i] <= len(nums) and nums[i] != nums[correct_pos]:
            nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
        else:
            i += 1
    
    for i in range(len(nums)):
        if nums[i] != i + 1:
            return i + 1
    
    return len(nums) + 1
```

## Common Techniques

### 1. Index Mapping
```python
def index_mapping_sort(nums):
    """Sort array where each number should be at index (number-1)"""
    for i in range(len(nums)):
        while nums[i] != i + 1 and 1 <= nums[i] <= len(nums):
            correct_pos = nums[i] - 1
            if nums[i] != nums[correct_pos]:
                nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
            else:
                break
```

### 2. Corruption Detection
```python
def find_corrupt_pair(nums):
    """Find the duplicate and missing number"""
    i = 0
    while i < len(nums):
        correct_pos = nums[i] - 1
        if nums[i] != nums[correct_pos]:
            nums[i], nums[correct_pos] = nums[correct_pos], nums[i]
        else:
            i += 1
    
    for i in range(len(nums)):
        if nums[i] != i + 1:
            return [nums[i], i + 1]
    
    return [-1, -1]
```

## Edge Cases to Consider
1. Empty array
2. Single element array
3. All elements same
4. Already sorted array
5. Reverse sorted array
6. Array with duplicates
7. Array with missing numbers
8. Numbers out of range
9. Negative numbers
10. Maximum value scenarios

## Common Pitfalls
1. Infinite loop in swapping
2. Not handling duplicates
3. Off-by-one errors
4. Not checking array bounds
5. Incorrect position calculation
6. Modifying input when not allowed
7. Not handling out-of-range values
8. Incorrect range assumptions

## Practice Problems by Difficulty

### Easy
1. [Missing Number](https://leetcode.com/problems/missing-number/) (LC #268)
2. [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) (LC #448)
3. [Set Mismatch](https://leetcode.com/problems/set-mismatch/) (LC #645)

### Medium
1. [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) (LC #287)
2. [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/) (LC #442)
3. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)

### Hard
1. [Couples Holding Hands](https://leetcode.com/problems/couples-holding-hands/) (LC #765)
2. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)
3. [N-Queens](https://leetcode.com/problems/n-queens/) (LC #51)

## Real-World Applications
1. **Error Detection**:
   - Finding corrupted data
   - Validating sequences
2. **Data Validation**:
   - Checking completeness
   - Identifying duplicates
3. **Resource Management**:
   - Memory allocation
   - Process scheduling
4. **Database Systems**:
   - Record deduplication
   - Data integrity checks
5. **Network Protocols**:
   - Packet sequence validation
   - Missing packet detection

## Advanced Topics
1. **Variants of Cyclic Sort**:
   - Multi-range sort
   - Negative number handling
2. **Optimization Techniques**:
   - Cache efficiency
   - Branch reduction
3. **Related Algorithms**:
   - Counting sort
   - Radix sort
4. **Applications in Other Algorithms**:
   - Graph cycle detection
   - Linked list cycle finding

## Important Resources
1. [Cyclic Sort Pattern](https://www.educative.io/courses/grokking-coding-interview-patterns-java/qVVNDRqLZZA)
2. [In-place Sorting](https://www.geeksforgeeks.org/in-place-algorithm/)
3. [Array Rearrangement](https://www.geeksforgeeks.org/rearrange-array-arrj-becomes-arri-j/)
4. [Missing Number Problems](https://leetcode.com/problems/missing-number/solution/)
5. [Duplicate Detection](https://leetcode.com/problems/find-the-duplicate-number/solution/)

## Interview Tips
1. Identify range constraints
2. Consider space requirements
3. Handle edge cases explicitly
4. Draw array state changes
5. Test with small examples
6. Consider optimization opportunities
7. Discuss time/space trade-offs
8. Handle invalid inputs
9. Consider follow-up questions
10. Think about scalability