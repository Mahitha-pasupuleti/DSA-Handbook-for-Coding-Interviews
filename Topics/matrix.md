# Matrix Data Structure and Algorithms 🧮

## Introduction
A matrix is a 2D array structure that organizes data in rows and columns. Matrix operations are fundamental in computer graphics, scientific computing, and many algorithmic problems. Understanding matrix manipulation is crucial for solving grid-based problems efficiently.

## Core Concepts

### Important Terminologies
- **Matrix**: 2D array of elements arranged in rows and columns
- **Row**: Horizontal line of elements
- **Column**: Vertical line of elements
- **Diagonal**: Elements where row index equals column index
- **Transpose**: Matrix flipped over its diagonal
- **Identity Matrix**: Square matrix with 1s on diagonal, 0s elsewhere
- **Sparse Matrix**: Matrix with mostly zero elements
- **Dense Matrix**: Matrix with mostly non-zero elements
- **Square Matrix**: Equal number of rows and columns
- **Rectangular Matrix**: Different number of rows and columns
- **Symmetric Matrix**: Equal to its transpose

### Matrix Properties
1. **Dimensions**: m × n (m rows, n columns)
2. **Access Pattern**: matrix[row][column]
3. **Memory Layout**: Contiguous in row-major or column-major order
4. **Common Operations**: Transpose, Rotation, Search, Traversal

### Time Complexity Analysis
| Operation               | Time Complexity | Space Complexity |
|------------------------|----------------|------------------|
| Access Element         | O(1)           | O(1)             |
| Row Traversal         | O(n)           | O(1)             |
| Column Traversal      | O(m)           | O(1)             |
| Matrix Multiplication | O(n³)          | O(n²)            |
| Transpose            | O(m×n)         | O(1) or O(m×n)   |
| Rotation             | O(m×n)         | O(1) or O(m×n)   |
| Search               | O(m×n)         | O(1)             |
| DFS/BFS              | O(m×n)         | O(m×n)           |

## Implementation Patterns

### 1. Matrix Creation and Basic Operations
```python
def create_matrix(rows, cols, default_value=0):
    return [[default_value] * cols for _ in range(rows)]

def print_matrix(matrix):
    for row in matrix:
        print(*row)

def transpose_matrix(matrix):
    return list(map(list, zip(*matrix)))

def get_dimensions(matrix):
    return len(matrix), len(matrix[0]) if matrix else 0
```

### 2. Matrix Rotation
```python
def rotate_90_clockwise(matrix):
    n = len(matrix)
    
    # Transpose
    for i in range(n):
        for j in range(i, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    
    # Reverse each row
    for i in range(n):
        matrix[i].reverse()

def rotate_90_counterclockwise(matrix):
    n = len(matrix)
    
    # Transpose
    for i in range(n):
        for j in range(i, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    
    # Reverse each column
    for j in range(n):
        for i in range(n//2):
            matrix[i][j], matrix[n-1-i][j] = matrix[n-1-i][j], matrix[i][j]
```

### 3. Spiral Traversal
```python
def spiral_order(matrix):
    if not matrix:
        return []
    
    result = []
    top, bottom = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1
    
    while top <= bottom and left <= right:
        # Traverse right
        for j in range(left, right + 1):
            result.append(matrix[top][j])
        top += 1
        
        # Traverse down
        for i in range(top, bottom + 1):
            result.append(matrix[i][right])
        right -= 1
        
        if top <= bottom:
            # Traverse left
            for j in range(right, left - 1, -1):
                result.append(matrix[bottom][j])
            bottom -= 1
        
        if left <= right:
            # Traverse up
            for i in range(bottom, top - 1, -1):
                result.append(matrix[i][left])
            left += 1
    
    return result
```

### 4. Matrix Search
```python
def search_sorted_matrix(matrix, target):
    if not matrix:
        return False
    
    m, n = len(matrix), len(matrix[0])
    row, col = 0, n - 1
    
    while row < m and col >= 0:
        if matrix[row][col] == target:
            return True
        elif matrix[row][col] > target:
            col -= 1
        else:
            row += 1
    
    return False
```

### 5. Island Problems (DFS)
```python
def num_islands(grid):
    if not grid:
        return 0
    
    def dfs(i, j):
        if (i < 0 or i >= len(grid) or 
            j < 0 or j >= len(grid[0]) or
            grid[i][j] != '1'):
            return
        
        grid[i][j] = '#'  # Mark as visited
        
        # Check all 4 directions
        dfs(i+1, j)
        dfs(i-1, j)
        dfs(i, j+1)
        dfs(i, j-1)
    
    count = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == '1':
                dfs(i, j)
                count += 1
    
    return count
```

## Common Techniques

### 1. Direction Arrays
```python
# 4 directions (up, right, down, left)
dx = [-1, 0, 1, 0]
dy = [0, 1, 0, -1]

# 8 directions (including diagonals)
dx8 = [-1, -1, -1, 0, 0, 1, 1, 1]
dy8 = [-1, 0, 1, -1, 1, -1, 0, 1]

def is_valid(x, y, rows, cols):
    return 0 <= x < rows and 0 <= y < cols
```

### 2. Layer by Layer Processing
```python
def process_matrix_layers(matrix):
    m, n = len(matrix), len(matrix[0])
    layers = min(m, n) // 2
    
    for layer in range(layers):
        first, last = layer, min(m, n) - 1 - layer
        for i in range(first, last):
            # Process current layer
            pass
```

## Edge Cases to Consider
1. Empty matrix
2. Single element matrix
3. Single row matrix
4. Single column matrix
5. Square vs rectangular matrix
6. Matrix with negative numbers
7. Matrix with duplicates
8. Sparse matrix
9. Identity matrix
10. Matrix with all same elements

## Common Pitfalls
1. Row/column index confusion
2. Out of bounds access
3. Incorrect rotation logic
4. Not handling empty matrix
5. Memory inefficient solutions
6. Incorrect traversal order
7. Missing edge cases
8. Modifying input when not allowed

## Practice Problems by Difficulty

### Easy
1. [Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/) (LC #1572)
2. [Flood Fill](https://leetcode.com/problems/flood-fill/) (LC #733)
3. [Transpose Matrix](https://leetcode.com/problems/transpose-matrix/) (LC #867)

### Medium
1. [Rotate Image](https://leetcode.com/problems/rotate-image/) (LC #48)
2. [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) (LC #54)
3. [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) (LC #73)
4. [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) (LC #74)

### Hard
1. [Word Search II](https://leetcode.com/problems/word-search-ii/) (LC #212)
2. [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/) (LC #37)
3. [Maximum Rectangle](https://leetcode.com/problems/maximal-rectangle/) (LC #85)

## Real-World Applications
1. **Image Processing**:
   - Pixel manipulation
   - Filters and transformations
2. **Computer Graphics**:
   - 2D transformations
   - Game board representations
3. **Scientific Computing**:
   - Linear algebra operations
   - Numerical methods
4. **Machine Learning**:
   - Feature matrices
   - Convolutional operations
5. **Game Development**:
   - Game boards
   - Collision detection
6. **Data Analysis**:
   - Correlation matrices
   - Heat maps

## Advanced Topics
1. **Matrix Optimization**:
   - Cache-friendly access
   - Memory-efficient storage
2. **Sparse Matrix Techniques**:
   - Compressed storage
   - Efficient operations
3. **Special Matrices**:
   - Toeplitz matrix
   - Circulant matrix
4. **Matrix Decomposition**:
   - LU decomposition
   - QR decomposition

## Important Resources
1. [Matrix Operations Tutorial](https://www.geeksforgeeks.org/matrix/)
2. [Efficient Matrix Manipulation](https://www.cs.cmu.edu/~scandal/cacm/node9.html)
3. [Sparse Matrix Algorithms](https://www.geeksforgeeks.org/sparse-matrix-representations/)
4. [Matrix Transformations](https://www.cs.cmu.edu/~462/projects/assn2/assn2/matrixfaq.html)
5. [NumPy Matrix Operations](https://numpy.org/doc/stable/reference/routines.array-manipulation.html)

## Interview Tips
1. Clarify matrix properties
2. Consider space optimization
3. Handle edge cases explicitly
4. Use direction arrays
5. Consider in-place operations
6. Draw examples
7. Test boundary conditions
8. Optimize traversal patterns
9. Consider symmetry properties
10. Discuss trade-offs