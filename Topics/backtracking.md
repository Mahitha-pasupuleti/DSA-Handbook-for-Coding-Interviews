# Backtracking Algorithm 🔙

## Introduction
Backtracking is an algorithmic technique that considers searching every possible combination in order to solve a computational problem. It builds candidates to the solution incrementally and abandons candidates ("backtracks") when it determines that the candidate cannot lead to a valid solution.

## Core Concepts

### Important Terminologies
- **Backtracking**: Algorithmic technique to find all solutions by incrementally building candidates
- **State Space Tree**: Tree representing all possible states
- **Pruning**: Eliminating branches that can't lead to solution
- **Constraint**: Condition that must be satisfied
- **Choice Point**: Point where decision is made
- **Dead End**: State that can't lead to solution
- **Solution Space**: Set of all possible solutions
- **Feasible Solution**: Solution satisfying all constraints
- **Optimal Solution**: Best solution among feasible ones
- **Decision Tree**: Tree showing all possible choices

### Time Complexity Analysis
| Problem Type        | Time Complexity | Space Complexity |
|--------------------|-----------------|------------------|
| Subsets            | O(2ⁿ)          | O(n)             |
| Permutations       | O(n!)          | O(n)             |
| N-Queens           | O(n!)          | O(n)             |
| Sudoku             | O(9^(n*n))     | O(n*n)          |
| Word Search        | O(4^(n*m))     | O(n*m)          |
| Combination Sum    | O(2^n)         | O(n)             |

Where n is the input size or board dimension

## Implementation Patterns

### 1. Basic Backtracking Template
```python
def backtrack(input, current_state, result):
    if is_solution(current_state):
        result.append(current_state.copy())
        return
    
    for choice in get_choices(input, current_state):
        if is_valid(choice, current_state):
            make_choice(choice, current_state)
            backtrack(input, current_state, result)
            undo_choice(choice, current_state)
```

### 2. Subset Generation
```python
def subsets(nums):
    def backtrack(start, path):
        result.append(path[:])
        
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i + 1, path)
            path.pop()
    
    result = []
    backtrack(0, [])
    return result
```

### 3. Permutation Generation
```python
def permutations(nums):
    def backtrack(path, used):
        if len(path) == len(nums):
            result.append(path[:])
            return
        
        for i in range(len(nums)):
            if not used[i]:
                used[i] = True
                path.append(nums[i])
                backtrack(path, used)
                path.pop()
                used[i] = False
    
    result = []
    backtrack([], [False] * len(nums))
    return result
```

### 4. N-Queens Problem
```python
def solveNQueens(n):
    def is_safe(board, row, col):
        # Check column
        for i in range(row):
            if board[i][col] == 'Q':
                return False
        
        # Check upper left diagonal
        for i, j in zip(range(row-1, -1, -1), range(col-1, -1, -1)):
            if board[i][j] == 'Q':
                return False
        
        # Check upper right diagonal
        for i, j in zip(range(row-1, -1, -1), range(col+1, n)):
            if board[i][j] == 'Q':
                return False
        
        return True
    
    def backtrack(row):
        if row == n:
            result.append([''.join(row) for row in board])
            return
        
        for col in range(n):
            if is_safe(board, row, col):
                board[row][col] = 'Q'
                backtrack(row + 1)
                board[row][col] = '.'
    
    board = [['.' for _ in range(n)] for _ in range(n)]
    result = []
    backtrack(0)
    return result
```

### 5. Combination Sum
```python
def combinationSum(candidates, target):
    def backtrack(start, target, path):
        if target < 0:
            return
        if target == 0:
            result.append(path[:])
            return
        
        for i in range(start, len(candidates)):
            path.append(candidates[i])
            backtrack(i, target - candidates[i], path)
            path.pop()
    
    result = []
    candidates.sort()  # Optional optimization
    backtrack(0, target, [])
    return result
```

## Common Techniques

### 1. State Management
```python
class State:
    def __init__(self):
        self.choices = []
        self.used = set()
    
    def make_choice(self, choice):
        self.choices.append(choice)
        self.used.add(choice)
    
    def undo_choice(self):
        choice = self.choices.pop()
        self.used.remove(choice)
    
    def is_valid(self, choice):
        return choice not in self.used
```

### 2. Pruning Optimization
```python
def backtrack_with_pruning(candidates, target, path, start):
    if target < 0:  # Pruning condition
        return
    if target == 0:
        result.append(path[:])
        return
    
    for i in range(start, len(candidates)):
        # Skip duplicates
        if i > start and candidates[i] == candidates[i-1]:
            continue
        
        # Pruning: if current number is too large
        if candidates[i] > target:
            break
        
        path.append(candidates[i])
        backtrack_with_pruning(candidates, target - candidates[i], path, i + 1)
        path.pop()
```

## Edge Cases to Consider
1. Empty input
2. Single element input
3. Duplicate elements
4. No solution exists
5. Multiple solutions
6. Maximum recursion depth
7. Large input size
8. All elements same
9. Negative numbers
10. Boundary conditions

## Common Pitfalls
1. Not handling base cases
2. Incorrect state management
3. Missing pruning opportunities
4. Infinite recursion
5. Memory overflow
6. Not copying state properly
7. Incorrect constraint checking
8. Inefficient pruning

## Practice Problems by Difficulty

### Easy
1. [Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/) (LC #784)
2. [Binary Watch](https://leetcode.com/problems/binary-watch/) (LC #401)
3. [Find Mode in Binary Search Tree](https://leetcode.com/problems/find-mode-in-binary-search-tree/) (LC #501)

### Medium
1. [Subsets](https://leetcode.com/problems/subsets/) (LC #78)
2. [Permutations](https://leetcode.com/problems/permutations/) (LC #46)
3. [Combination Sum](https://leetcode.com/problems/combination-sum/) (LC #39)
4. [Word Search](https://leetcode.com/problems/word-search/) (LC #79)

### Hard
1. [N-Queens](https://leetcode.com/problems/n-queens/) (LC #51)
2. [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/) (LC #37)
3. [Word Search II](https://leetcode.com/problems/word-search-ii/) (LC #212)

## Real-World Applications
1. **Constraint Satisfaction**:
   - Scheduling problems
   - Resource allocation
2. **Game Playing**:
   - Chess engines
   - Puzzle solvers
3. **Circuit Design**:
   - VLSI design
   - Path routing
4. **AI and Machine Learning**:
   - Decision trees
   - Neural architecture search
5. **Operations Research**:
   - Vehicle routing
   - Facility location
6. **Bioinformatics**:
   - Protein folding
   - Gene sequencing

## Advanced Topics
1. **Parallel Backtracking**:
   - Task parallelization
   - Load balancing
2. **Hybrid Approaches**:
   - Backtracking with DP
   - Backtracking with Branch & Bound
3. **Optimization Techniques**:
   - Forward checking
   - Constraint propagation
4. **Heuristic Functions**:
   - State ordering
   - Variable ordering

## Important Resources
1. [Backtracking Algorithms](https://www.geeksforgeeks.org/backtracking-algorithms/)
2. [Constraint Satisfaction Problems](https://www.geeksforgeeks.org/constraint-satisfaction-problems-csp-in-artificial-intelligence/)
3. [Optimization Techniques](https://www.geeksforgeeks.org/backtracking-introduction/)
4. [Pattern Recognition](https://leetcode.com/discuss/general-discussion/136503/backtracking-pattern)
5. [Visual Backtracking](https://www.cs.usfca.edu/~galles/visualization/DFS.html)

## Interview Tips
1. Identify problem constraints
2. Draw state space tree
3. Consider pruning opportunities
4. Handle base cases properly
5. Manage state carefully
6. Consider optimization techniques
7. Test with small examples
8. Analyze time complexity
9. Consider space optimization
10. Discuss trade-offs