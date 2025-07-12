# Greedy Algorithms 💰

## Introduction
A greedy algorithm makes the locally optimal choice at each step, hoping to find a global optimum. While not always yielding the optimal solution, greedy algorithms are often used for optimization problems and can be both efficient and effective when the problem has optimal substructure and the greedy choice property.

## Core Concepts

### Important Terminologies
- **Greedy Choice Property**: Local optimal choice leads to global optimum
- **Optimal Substructure**: Problem's optimal solution contains optimal sub-solutions
- **Local Optimum**: Best choice at current step
- **Global Optimum**: Best overall solution
- **Feasible Solution**: Solution satisfying all constraints
- **Candidate Solution**: Potential solution being considered
- **Selection Function**: Chooses best candidate
- **Feasibility Function**: Checks if choice is valid
- **Objective Function**: Value to be optimized
- **Solution Space**: Set of all possible solutions

### Properties of Greedy Algorithms
1. **Makes Irrevocable Choices**: Decisions once made are final
2. **No Backtracking**: Never reconsiders choices
3. **Locally Optimal**: Best choice at each step
4. **Hope for Global Optimum**: May or may not achieve it
5. **Polynomial Time**: Usually efficient

### Time Complexity Analysis
| Problem Type           | Time Complexity | Space Complexity |
|-----------------------|-----------------|------------------|
| Activity Selection    | O(n log n)      | O(1)            |
| Huffman Coding       | O(n log n)      | O(n)            |
| Fractional Knapsack  | O(n log n)      | O(1)            |
| Minimum Spanning Tree| O(E log V)      | O(V)            |
| Dijkstra's Algorithm | O(V² + E)       | O(V)            |
| Job Scheduling       | O(n log n)      | O(1)            |

## Implementation Patterns

### 1. Activity Selection
```python
def activity_selection(start, finish):
    # Sort by finish time
    activities = sorted(zip(start, finish), key=lambda x: x[1])
    selected = [activities[0]]
    last_finish = activities[0][1]
    
    for i in range(1, len(activities)):
        if activities[i][0] >= last_finish:
            selected.append(activities[i])
            last_finish = activities[i][1]
    
    return selected
```

### 2. Fractional Knapsack
```python
def fractional_knapsack(values, weights, capacity):
    # Calculate value per unit weight
    ratios = [(v/w, v, w) for v, w in zip(values, weights)]
    ratios.sort(reverse=True)
    
    total_value = 0
    remaining_capacity = capacity
    
    for ratio, value, weight in ratios:
        if remaining_capacity >= weight:
            total_value += value
            remaining_capacity -= weight
        else:
            total_value += ratio * remaining_capacity
            break
    
    return total_value
```

### 3. Huffman Coding
```python
import heapq

class Node:
    def __init__(self, char, freq):
        self.char = char
        self.freq = freq
        self.left = None
        self.right = None
    
    def __lt__(self, other):
        return self.freq < other.freq

def huffman_coding(chars, freqs):
    heap = []
    for char, freq in zip(chars, freqs):
        heapq.heappush(heap, Node(char, freq))
    
    while len(heap) > 1:
        left = heapq.heappop(heap)
        right = heapq.heappop(heap)
        
        internal = Node(None, left.freq + right.freq)
        internal.left = left
        internal.right = right
        
        heapq.heappush(heap, internal)
    
    return heap[0]
```

### 4. Interval Scheduling
```python
def interval_scheduling(intervals):
    # Sort by end time
    intervals.sort(key=lambda x: x[1])
    
    selected = []
    current_end = float('-inf')
    
    for start, end in intervals:
        if start >= current_end:
            selected.append([start, end])
            current_end = end
    
    return selected
```

### 5. Job Sequencing with Deadlines
```python
def job_sequencing(jobs, deadlines, profits):
    # Sort jobs by profit in descending order
    job_info = sorted(zip(jobs, deadlines, profits),
                     key=lambda x: x[2], reverse=True)
    
    max_deadline = max(deadlines)
    slot = [-1] * max_deadline
    
    for job, deadline, profit in job_info:
        for j in range(deadline-1, -1, -1):
            if slot[j] == -1:
                slot[j] = job
                break
    
    return [x for x in slot if x != -1]
```

## Common Techniques

### 1. Sort-First Strategy
```python
def minimum_coins(coins, amount):
    coins.sort(reverse=True)
    count = 0
    remaining = amount
    
    for coin in coins:
        count += remaining // coin
        remaining %= coin
    
    return count if remaining == 0 else -1
```

### 2. Priority Queue Approach
```python
def minimum_cost_ropes(ropes):
    heapq.heapify(ropes)
    total_cost = 0
    
    while len(ropes) > 1:
        first = heapq.heappop(ropes)
        second = heapq.heappop(ropes)
        cost = first + second
        total_cost += cost
        heapq.heappush(ropes, cost)
    
    return total_cost
```

## Edge Cases to Consider
1. Empty input
2. Single element
3. All elements same
4. Extreme values
5. Negative numbers
6. Overlapping intervals
7. Conflicting priorities
8. Ties in selection
9. Maximum capacity
10. Invalid input

## Common Pitfalls
1. Assuming greedy always works
2. Not proving greedy property
3. Incorrect sorting criteria
4. Missing edge cases
5. Not handling ties properly
6. Overflow/underflow
7. Incorrect priority assignment
8. Not considering constraints

## Practice Problems by Difficulty

### Easy
1. [Assign Cookies](https://leetcode.com/problems/assign-cookies/) (LC #455)
2. [Lemonade Change](https://leetcode.com/problems/lemonade-change/) (LC #860)
3. [Maximum Units on a Truck](https://leetcode.com/problems/maximum-units-on-a-truck/) (LC #1710)

### Medium
1. [Jump Game](https://leetcode.com/problems/jump-game/) (LC #55)
2. [Partition Labels](https://leetcode.com/problems/partition-labels/) (LC #763)
3. [Task Scheduler](https://leetcode.com/problems/task-scheduler/) (LC #621)
4. [Gas Station](https://leetcode.com/problems/gas-station/) (LC #134)

### Hard
1. [Candy](https://leetcode.com/problems/candy/) (LC #135)
2. [Course Schedule III](https://leetcode.com/problems/course-schedule-iii/) (LC #630)
3. [Split Array into Consecutive Subsequences](https://leetcode.com/problems/split-array-into-consecutive-subsequences/) (LC #659)

## Real-World Applications
1. **Networking**:
   - Routing protocols
   - Channel allocation
2. **Operating Systems**:
   - Process scheduling
   - Memory allocation
3. **Data Compression**:
   - Huffman coding
   - Run-length encoding
4. **Financial Markets**:
   - Trading strategies
   - Portfolio optimization
5. **Resource Management**:
   - Task scheduling
   - Load balancing
6. **Logistics**:
   - Vehicle routing
   - Warehouse optimization

## Advanced Topics
1. **Approximation Algorithms**:
   - Set cover
   - Traveling salesman
2. **Online Algorithms**:
   - Competitive analysis
   - Stream processing
3. **Randomized Greedy**:
   - Probabilistic choices
   - Monte Carlo methods
4. **Multi-objective Greedy**:
   - Pareto optimality
   - Trade-off analysis

## Important Resources
1. [Introduction to Greedy Algorithms](https://www.geeksforgeeks.org/greedy-algorithms/)
2. [Activity Selection Problem](https://www.geeksforgeeks.org/activity-selection-problem-greedy-algo-1/)
3. [Huffman Coding Tutorial](https://www.geeksforgeeks.org/huffman-coding-greedy-algo-3/)
4. [Interval Scheduling](https://www.cs.princeton.edu/~wayne/kleinberg-tardos/pdf/04GreedyAlgorithmsI.pdf)
5. [Minimum Spanning Trees](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)

## Interview Tips
1. Prove greedy choice property
2. Consider counter-examples
3. Compare with dynamic programming
4. Analyze time complexity
5. Handle edge cases
6. Consider sorting first
7. Use priority queues when needed
8. Test with small examples
9. Optimize space usage
10. Discuss trade-offs