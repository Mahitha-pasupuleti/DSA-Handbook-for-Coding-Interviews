# Dynamic Programming 🧠

## Introduction
Dynamic Programming (DP) is a method for solving complex problems by breaking them down into simpler subproblems. It is applicable when subproblems overlap and have optimal substructure. DP combines the solutions to subproblems to solve the original problem.

## Core Concepts

### Important Terminologies
- **Overlapping Subproblems**: Same subproblems occur repeatedly
- **Optimal Substructure**: Optimal solution contains optimal subsolutions
- **State**: Variables needed to uniquely identify subproblem
- **Transition**: Way to move from one state to another
- **Base Case**: Smallest subproblem with known solution
- **Memoization**: Top-down approach with recursion + caching
- **Tabulation**: Bottom-up approach with iteration
- **State Space**: Set of all possible states
- **Recurrence Relation**: Formula relating states
- **Subproblem Graph**: Dependencies between subproblems

### Approaches to DP
1. **Top-Down (Memoization)**:
   - Recursive approach
   - Cache results
   - Natural to implement
   - Stack space overhead

2. **Bottom-Up (Tabulation)**:
   - Iterative approach
   - Build table
   - More space efficient
   - Order of computation important

### Time and Space Complexity Analysis
| Pattern                    | Time Complexity | Space Complexity |
|---------------------------|-----------------|------------------|
| Linear DP                 | O(n)           | O(n)             |
| Matrix Chain              | O(n³)          | O(n²)            |
| 0/1 Knapsack             | O(nW)          | O(nW)            |
| LCS                      | O(mn)          | O(mn)            |
| Edit Distance            | O(mn)          | O(mn)            |
| Matrix Path              | O(mn)          | O(mn)            |
| Coin Change              | O(nA)          | O(A)             |
| Longest Increasing Seq   | O(n²)          | O(n)             |

Where:
- n, m = input sizes
- W = weight capacity
- A = target amount

## Implementation Patterns

### 1. Fibonacci with Both Approaches
```python
# Top-down (Memoization)
def fib_memo(n, memo=None):
    if memo is None:
        memo = {}
    
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return n
    
    memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo)
    return memo[n]

# Bottom-up (Tabulation)
def fib_tab(n):
    if n <= 1:
        return n
    
    dp = [0] * (n + 1)
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    
    return dp[n]
```

### 2. 0/1 Knapsack
```python
def knapsack(values, weights, capacity):
    n = len(values)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            if weights[i-1] <= w:
                dp[i][w] = max(
                    values[i-1] + dp[i-1][w-weights[i-1]],  # Take item
                    dp[i-1][w]  # Skip item
                )
            else:
                dp[i][w] = dp[i-1][w]
    
    return dp[n][capacity]
```

### 3. Longest Common Subsequence
```python
def lcs(text1: str, text2: str) -> int:
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i-1] == text2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    
    return dp[m][n]
```

### 4. Matrix Path Problems
```python
def min_path_sum(grid):
    if not grid:
        return 0
    
    m, n = len(grid), len(grid[0])
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = grid[0][0]
    
    # Fill first row
    for j in range(1, n):
        dp[0][j] = dp[0][j-1] + grid[0][j]
    
    # Fill first column
    for i in range(1, m):
        dp[i][0] = dp[i-1][0] + grid[i][0]
    
    # Fill rest of the table
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
    
    return dp[m-1][n-1]
```

### 5. State Compression DP
```python
def can_partition(nums):
    total = sum(nums)
    if total % 2:
        return False
    
    target = total // 2
    dp = 1 << target
    
    for num in nums:
        dp |= (dp << num) & ((1 << (target + 1)) - 1)
    
    return dp & (1 << target)
```

## Common DP Patterns

### 1. Linear DP
- One-dimensional state
- Linear state transition
- Example: Fibonacci, Climbing Stairs

### 2. Matrix DP
- Two-dimensional state
- Grid-based problems
- Example: Unique Paths, Minimum Path Sum

### 3. Interval DP
- State represents interval
- Usually O(n²) or O(n³)
- Example: Matrix Chain Multiplication

### 4. Decision Making
- Choose or not choose at each step
- Example: House Robber, 0/1 Knapsack

### 5. String DP
- States based on string indices
- Example: Edit Distance, LCS

## Edge Cases to Consider
1. Empty input
2. Single element input
3. Negative numbers
4. Integer overflow
5. Maximum recursion depth
6. Large input size
7. Equal values
8. Boundary conditions
9. Invalid input
10. Memory constraints

## Common Pitfalls
1. Incorrect base cases
2. Missing state variables
3. Wrong recurrence relation
4. Not handling edge cases
5. Inefficient state representation
6. Memory limit exceeded
7. Stack overflow in recursion
8. Incorrect initialization

## Practice Problems by Difficulty

### Easy
1. [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) (LC #70)
2. [House Robber](https://leetcode.com/problems/house-robber/) (LC #198)
3. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) (LC #121)

### Medium
1. [Unique Paths](https://leetcode.com/problems/unique-paths/) (LC #62)
2. [Coin Change](https://leetcode.com/problems/coin-change/) (LC #322)
3. [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) (LC #300)
4. [Target Sum](https://leetcode.com/problems/target-sum/) (LC #494)

### Hard
1. [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/) (LC #10)
2. [Edit Distance](https://leetcode.com/problems/edit-distance/) (LC #72)
3. [Burst Balloons](https://leetcode.com/problems/burst-balloons/) (LC #312)

## Real-World Applications
1. **Resource Allocation**:
   - Job scheduling
   - Memory management
2. **Financial Planning**:
   - Investment strategies
   - Portfolio optimization
3. **Bioinformatics**:
   - Sequence alignment
   - Protein folding
4. **Game Theory**:
   - Optimal strategies
   - Decision making
5. **Computer Graphics**:
   - Image processing
   - Path finding
6. **Natural Language Processing**:
   - Text similarity
   - Speech recognition

## Advanced Topics
1. **Probability DP**:
   - Expected value
   - State probability
2. **Tree DP**:
   - Tree diameter
   - Tree coloring
3. **Bitmask DP**:
   - State compression
   - Subset problems
4. **Digit DP**:
   - Number range problems
   - Digit counting
5. **Connection with Other Techniques**:
   - DP with binary search
   - DP with segment trees

## Important Resources
1. [Dynamic Programming Patterns](https://leetcode.com/discuss/general-discussion/458695/dynamic-programming-patterns)
2. [How to Solve DP Problems](https://www.freecodecamp.org/news/demystifying-dynamic-programming-3efafb8d4296/)
3. [TopCoder DP Tutorial](https://www.topcoder.com/community/competitive-programming/tutorials/dynamic-programming-from-novice-to-advanced/)
4. [Algorithms Live! DP](https://www.youtube.com/watch?v=YBSt1jYwVfU)
5. [MIT OpenCourseWare DP](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/lecture-videos/lecture-19-dynamic-programming-i-fibonacci-shortest-paths/)

## Interview Tips
1. Identify overlapping subproblems
2. Define clear state representation
3. Write recurrence relation
4. Consider space optimization
5. Handle base cases properly
6. Draw state transition diagram
7. Test with small examples
8. Analyze time/space complexity
9. Consider both approaches
10. Optimize final solution