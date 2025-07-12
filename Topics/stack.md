# Stack Data Structure 🧱

## Introduction
A stack is a fundamental data structure that follows the Last-In-First-Out (LIFO) principle. Think of it like a stack of plates - you can only add or remove plates from the top.

## Core Concepts

### Important Terminologies
- **Stack**: A LIFO (Last-In-First-Out) data structure
- **Push**: Operation to add an element to the top of stack
- **Pop**: Operation to remove the top element from stack
- **Peek/Top**: Operation to view the top element without removing it
- **Stack Overflow**: When trying to push to a full stack
- **Stack Underflow**: When trying to pop from an empty stack
- **MinStack**: Stack with O(1) minimum element access
- **Monotonic Stack**: Stack maintaining increasing/decreasing order

### Time Complexity Analysis
| Operation | Average Case | Worst Case |
|-----------|--------------|------------|
| Push      | O(1)         | O(1)       |
| Pop       | O(1)         | O(1)       |
| Peek      | O(1)         | O(1)       |
| Search    | O(n)         | O(n)       |
| isEmpty   | O(1)         | O(1)       |

### Space Complexity
- **Basic Stack**: O(n) where n is number of elements
- **MinStack**: O(n) for maintaining minimum values
- **Call Stack**: O(h) where h is recursion depth

## Implementation

### Basic Stack Implementation
```python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        self.items.append(item)
    
    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        raise IndexError("Pop from empty stack")
    
    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        raise IndexError("Peek at empty stack")
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)
```

### MinStack Implementation
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []
    
    def push(self, val):
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)
    
    def pop(self):
        if self.stack:
            if self.stack[-1] == self.min_stack[-1]:
                self.min_stack.pop()
            return self.stack.pop()
    
    def get_min(self):
        return self.min_stack[-1] if self.min_stack else None
```

## Common Applications

### 1. Expression Evaluation
```python
def evaluate_rpn(tokens):
    stack = []
    operators = {'+': lambda x,y: x+y, '-': lambda x,y: x-y,
                '*': lambda x,y: x*y, '/': lambda x,y: int(x/y)}
    
    for token in tokens:
        if token in operators:
            b, a = stack.pop(), stack.pop()
            stack.append(operators[token](a, b))
        else:
            stack.append(int(token))
    
    return stack[0]
```

### 2. Parentheses Matching
```python
def is_valid_parentheses(s):
    stack = []
    pairs = {')': '(', '}': '{', ']': '['}
    
    for char in s:
        if char in '({[':
            stack.append(char)
        elif char in ')}]':
            if not stack or stack.pop() != pairs[char]:
                return False
    
    return len(stack) == 0
```

## Common Patterns

### 1. Monotonic Stack Pattern
Used for finding next greater/smaller element problems.
```python
def next_greater_element(nums):
    result = [-1] * len(nums)
    stack = []  # stores indices
    
    for i in range(len(nums)):
        while stack and nums[i] > nums[stack[-1]]:
            result[stack.pop()] = nums[i]
        stack.append(i)
    
    return result
```

### 2. Calculator Pattern
Used for basic calculator problems.
```python
def calculate(s):
    stack = []
    num = 0
    sign = 1
    result = 0
    
    for char in s + '+':
        if char.isdigit():
            num = num * 10 + int(char)
        elif char in '+-':
            result += sign * num
            num = 0
            sign = 1 if char == '+' else -1
    
    return result
```

## Edge Cases to Consider
1. Empty stack operations
2. Stack with single element
3. Stack reaching maximum capacity
4. Invalid input formats
5. Nested expressions
6. Multiple valid solutions
7. Negative numbers in calculations

## Common Pitfalls
1. Forgetting to handle empty stack
2. Not considering operator precedence
3. Incorrect handling of negative numbers
4. Stack overflow in recursion
5. Not clearing stack between test cases

## Practice Problems by Difficulty

### Easy
1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) (LC #20)
2. [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/) (LC #225)
3. [Baseball Game](https://leetcode.com/problems/baseball-game/) (LC #682)

### Medium
1. [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) (LC #150)
2. [Min Stack](https://leetcode.com/problems/min-stack/) (LC #155)
3. [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) (LC #739)
4. [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/) (LC #503)

### Hard
1. [Basic Calculator](https://leetcode.com/problems/basic-calculator/) (LC #224)
2. [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) (LC #84)
3. [Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/) (LC #895)

## Real-World Applications
1. **Browser History**: Back/Forward navigation
2. **Undo/Redo**: Text editors and graphic software
3. **Expression Evaluation**: Calculators and compilers
4. **Memory Management**: Call stack in programming languages
5. **Syntax Parsing**: Compiler design and validation

## Advanced Topics
1. **Thread-Safe Stacks**: Concurrent implementations
2. **Memory Efficient Stacks**: Using linked lists
3. **Custom Stack Implementations**:
   - Bounded Stack
   - Circular Stack
   - Double Stack

## Important Resources
1. [Stack Data Structure](https://www.geeksforgeeks.org/stack-data-structure/)
2. [Monotonic Stack Pattern](https://leetcode.com/problems/daily-temperatures/solution/)
3. [Stack Implementation Guide](https://www.programiz.com/dsa/stack)
4. [Stack Applications](https://www.geeksforgeeks.org/applications-of-stack-data-structure/)
5. [Stack in Standard Libraries](https://docs.python.org/3/library/collections.html#collections.deque)

## Interview Tips
1. Always validate input constraints
2. Consider time/space complexity requirements
3. Handle edge cases explicitly
4. Use built-in implementations when allowed
5. Consider stack variations (min stack, monotonic stack)
6. Test your solution with boundary conditions