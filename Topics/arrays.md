# Arrays in Data Structures and Algorithms 📌

## Introduction
Arrays are fundamental data structures that store elements in contiguous memory locations. They are the building blocks for many other data structures and algorithms.

## Core Concepts

### Important Terminologies
- **Array**: A collection of elements stored at contiguous memory locations
- **Subarray**: Contiguous elements within an array (e.g., [1,2,3] in [1,2,3,4])
- **Subsequence**: Non-contiguous elements maintaining relative order (e.g., [1,3,4] in [1,2,3,4])
- **Bitonic Array**: Array which first increases then decreases (e.g., [1,3,5,4,2])
- **Circular Array**: Array where we consider the first element as next to the last element

### Time Complexity Analysis
| Operation | Average Case | Worst Case |
|-----------|--------------|------------|
| Access    | O(1)         | O(1)       |
| Search    | O(n)         | O(n)       |
| Insertion | O(n)         | O(n)       |
| Deletion  | O(n)         | O(n)       |
| Sort      | O(n log n)   | O(n²)      |

### Space Complexity
- **Linear Arrays**: O(n) where n is the size of array
- **2D Arrays**: O(m×n) where m and n are dimensions

## Common Techniques

### 1. Two Pointer Technique
Used when dealing with sorted arrays or pairs in array.
```python
def twoSum(nums, target):
    left, right = 0, len(nums) - 1
    while left < right:
        curr_sum = nums[left] + nums[right]
        if curr_sum == target:
            return [left, right]
        elif curr_sum < target:
            left += 1
        else:
            right -= 1
    return []
```

### 2. Sliding Window
Useful for problems involving contiguous subarrays.
```python
def maxSumSubarray(nums, k):
    window_sum = sum(nums[:k])
    max_sum = window_sum
    
    for i in range(len(nums) - k):
        window_sum = window_sum - nums[i] + nums[i + k]
        max_sum = max(max_sum, window_sum)
    
    return max_sum
```

### 3. Prefix Sum
Optimal for range queries and cumulative computations.
```python
def buildPrefixSum(nums):
    prefix = [0] * (len(nums) + 1)
    for i in range(len(nums)):
        prefix[i + 1] = prefix[i] + nums[i]
    return prefix
```

### 4. Kadane's Algorithm
For maximum subarray problems.
```python
def kadane(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum
```

## Edge Cases to Consider
- Empty array
- Array with single element
- Array with all negative values
- Array with duplicates
- Array with overflow potential
- Sorted vs unsorted arrays
- Circular array scenarios

## Common Pitfalls
1. Off-by-one errors in array indexing
2. Not handling array bounds properly
3. Assuming array is sorted when it's not
4. Ignoring integer overflow
5. Not considering memory constraints for large arrays

## Practice Problems by Difficulty

### Easy
1. [Two Sum](https://leetcode.com/problems/two-sum/) (LC #1)
2. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) (LC #121)
3. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (LC #217)

### Medium
1. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) (LC #53)
2. [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/) (LC #438)
3. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) (LC #11)
4. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) (LC #560)

### Hard
1. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC #41)
2. [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) (LC #4)
3. [Maximum Rectangle](https://leetcode.com/problems/maximal-rectangle/) (LC #85)

## Real-World Applications
1. **Image Processing**: Pixels in images are stored as 2D arrays
2. **Database Systems**: Array-based indices for faster lookups
3. **Memory Management**: Contiguous memory allocation
4. **Video Games**: Collision detection using grid arrays
5. **Scientific Computing**: Matrix operations in numerical analysis

## Advanced Topics
1. **Dynamic Arrays**: Implementation and amortized analysis
2. **Sparse Arrays**: Efficient storage for arrays with many default values
3. **Array-based Data Structures**: 
   - Heap
   - Hash Table
   - Stack
   - Queue

## Important Resources
1. [Python Arrays Documentation](https://docs.python.org/3/library/array.html)
2. [Python bisect module](https://docs.python.org/3/library/bisect.html)
3. [Sliding Window Technique](https://leetcode.com/problems/minimum-size-subarray-sum/solution/)
4. [Prefix Sum Array Tutorial](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/)
5. [Two Pointer Technique](https://leetcode.com/articles/two-pointer-technique/)

## Interview Tips
1. Always clarify input constraints and array properties
2. Consider time/space complexity requirements
3. Look for sorting requirements or if input is already sorted
4. Consider using standard library functions when appropriate
5. Test your solution with edge cases before finalizing