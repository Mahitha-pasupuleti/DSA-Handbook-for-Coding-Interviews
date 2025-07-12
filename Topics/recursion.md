# Recursion in Programming 🔁

## Introduction
Recursion is a programming concept where a function solves a problem by calling itself with smaller instances of the same problem. It's a powerful technique for solving problems that can be broken down into smaller, similar sub-problems.

## Core Concepts

### Important Terminologies
- **Base Case**: Condition where recursion stops
- **Recursive Case**: Function calling itself
- **Call Stack**: Memory storing function calls
- **Stack Frame**: Memory for single function call
- **Recursion Depth**: Number of recursive calls
- **Direct Recursion**: Function calls itself directly
- **Indirect Recursion**: Function A calls B, B calls A
- **Tail Recursion**: Recursive call is last operation
- **Tree Recursion**: Multiple recursive calls
- **Nested Recursion**: Recursive parameter is recursive

### Types of Recursion
1. **Linear Recursion**: One recursive call per function
2. **Binary Recursion**: Two recursive calls per function
3. **Multiple Recursion**: Multiple recursive calls
4. **Mutual Recursion**: Functions calling each other
5. **Nested Recursion**: Parameter is recursive call

### Time and Space Complexity Analysis
| Type           | Time Complexity | Space Complexity |
|----------------|----------------|------------------|
| Linear         | O(n)           | O(n)             |
| Binary         | O(2^n)         | O(n)             |
| Tail           | O(n)           | O(1)*            |
| Tree           | O(branches^depth)| O(depth)        |
| Nested         | Varies         | O(depth)         |

*Note: O(1) space for tail recursion only with proper optimization (not available in Python)

## Implementation Patterns

### 1. Basic Linear Recursion
```python
def factorial(n):
    # Base case
    if n <= 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```

### 2. Tail Recursion
```python
def factorial_tail(n, accumulator=1):
    if n <= 1:
        return accumulator
    return factorial_tail(n - 1, n * accumulator)

def fibonacci_tail(n, a=0, b=1):
    if n == 0:
        return a
    return fibonacci_tail(n - 1, b, a + b)
```

### 3. Binary Recursion (Divide and Conquer)
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

### 4. Tree Recursion
```python
def print_binary_strings(n, string=""):
    if len(string) == n:
        print(string)
        return
    
    print_binary_strings(n, string + "0")
    print_binary_strings(n, string + "1")

def generate_permutations(string, prefix=""):
    if len(string) == 0:
        print(prefix)
        return
    
    for i in range(len(string)):
        rem = string[:i] + string[i+1:]
        generate_permutations(rem, prefix + string[i])
```

### 5. Memoization with Recursion
```python
def fibonacci_memo(n, memo=None):
    if memo is None:
        memo = {}
    
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return n
    
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]
```

## Common Techniques

### 1. Backtracking Template
```python
def backtrack(candidates, target, path, results):
    if target < 0:
        return
    if target == 0:
        results.append(path[:])
        return
    
    for i in range(len(candidates)):
        path.append(candidates[i])
        backtrack(candidates[i:], target - candidates[i], path, results)
        path.pop()
```

### 2. Tree Traversal
```python
def tree_traversal(root):
    if not root:
        return
    
    # Pre-order
    print(root.val)
    tree_traversal(root.left)
    tree_traversal(root.right)
```

## Edge Cases to Consider
1. Base case not reached
2. Stack overflow
3. Negative or zero input
4. Empty input
5. Single element input
6. Maximum recursion depth
7. Circular dependencies
8. Duplicate calculations
9. Large input causing deep recursion
10. Memory constraints

## Common Pitfalls
1. Missing base case
2. Incorrect base case
3. Infinite recursion
4. Not handling edge cases
5. Inefficient recursive solution
6. Stack overflow
7. Redundant calculations
8. Memory leaks

## Practice Problems by Difficulty

### Easy
1. [Power of Three](https://leetcode.com/problems/power-of-three/) (LC #326)
2. [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) (LC #509)
3. [Reverse String](https://leetcode.com/problems/reverse-string/) (LC #344)

### Medium
1. [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) (LC #22)
2. [Pow(x, n)](https://leetcode.com/problems/powx-n/) (LC #50)
3. [Subsets](https://leetcode.com/problems/subsets/) (LC #78)
4. [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) (LC #17)

### Hard
1. [N-Queens](https://leetcode.com/problems/n-queens/) (LC #51)
2. [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/) (LC #10)
3. [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/) (LC #37)

## Real-World Applications
1. **File Systems**: Directory traversal
2. **Compilers**: Expression parsing
3. **Graphics**: Fractal generation
4. **AI/ML**: Tree-based algorithms
5. **Games**: Game tree exploration
6. **Mathematics**: Mathematical induction
7. **Data Processing**: XML/JSON parsing

## Advanced Topics
1. **Tail Call Optimization**:
   - Implementation
   - Language support
   - Limitations
2. **Recursion to Iteration**:
   - Stack simulation
   - State machines
3. **Memory Management**:
   - Stack vs Heap
   - Memory optimization
4. **Parallel Recursion**:
   - Task parallelization
   - Work stealing

## Important Resources
1. [Recursion Visualization](https://recursion.now.sh/)
2. [Python Recursion Guide](https://realpython.com/python-recursion/)
3. [Tail Call Optimization](https://www.geeksforgeeks.org/tail-recursion/)
4. [Recursion vs Iteration](https://www.geeksforgeeks.org/recursion-vs-iteration/)
5. [Memory Management in Recursion](https://www.geeksforgeeks.org/memory-allocation-in-recursion/)

## Interview Tips
1. Always identify base cases first
2. Consider time/space complexity
3. Look for recursive patterns
4. Consider iterative alternatives
5. Handle edge cases explicitly
6. Use visualization for complex cases
7. Consider memoization
8. Test with small examples
9. Discuss optimization possibilities
10. Consider stack limitations