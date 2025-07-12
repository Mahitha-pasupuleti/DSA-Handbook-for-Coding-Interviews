# Interval Problems and Algorithms 📆

## Introduction
Interval problems involve ranges defined by start and end points. These problems are common in scheduling, resource allocation, and time management applications. Understanding interval manipulation and algorithms is crucial for solving real-world optimization problems.

## Core Concepts

### Important Terminologies
- **Interval**: Range defined by start and end points
- **Overlapping**: Intervals that intersect
- **Disjoint**: Non-overlapping intervals
- **Merge**: Combining overlapping intervals
- **Intersection**: Common range between intervals
- **Union**: Combined range of intervals
- **Nested**: One interval completely inside another
- **Adjacent**: Intervals that touch but don't overlap
- **Coverage**: Total range covered by intervals
- **Gap**: Space between non-overlapping intervals

### Types of Interval Problems
1. **Overlap Detection**: Find if intervals overlap
2. **Merging**: Combine overlapping intervals
3. **Scheduling**: Find maximum non-overlapping intervals
4. **Resource Allocation**: Track simultaneous intervals
5. **Coverage**: Find total covered range

### Time Complexity Analysis
| Operation               | Time Complexity | Space Complexity |
|------------------------|----------------|------------------|
| Sort Intervals         | O(n log n)     | O(1) or O(n)    |
| Merge Intervals        | O(n)           | O(n)            |
| Find Overlaps         | O(n log n)     | O(n)            |
| Maximum Non-overlapping| O(n log n)     | O(1)            |
| Meeting Rooms         | O(n log n)     | O(n)            |
| Insert Interval       | O(n)           | O(n)            |

## Implementation Patterns

### 1. Basic Interval Operations
```python
class Interval:
    def __init__(self, start, end):
        self.start = start
        self.end = end

def do_overlap(a: Interval, b: Interval) -> bool:
    return max(a.start, b.start) <= min(a.end, b.end)

def get_overlap(a: Interval, b: Interval) -> Interval:
    if not do_overlap(a, b):
        return None
    return Interval(max(a.start, b.start), min(a.end, b.end))

def merge_two_intervals(a: Interval, b: Interval) -> Interval:
    if not do_overlap(a, b):
        return None
    return Interval(min(a.start, b.start), max(a.end, b.end))
```

### 2. Merge Intervals
```python
def merge_intervals(intervals):
    if not intervals:
        return []
    
    # Sort by start time
    intervals.sort(key=lambda x: x[0])
    
    merged = [intervals[0]]
    
    for interval in intervals[1:]:
        if interval[0] <= merged[-1][1]:
            # Overlapping intervals, update end time
            merged[-1][1] = max(merged[-1][1], interval[1])
        else:
            # Non-overlapping interval, add to result
            merged.append(interval)
    
    return merged
```

### 3. Meeting Rooms
```python
import heapq

def min_meeting_rooms(intervals):
    if not intervals:
        return 0
    
    # Sort by start time
    intervals.sort(key=lambda x: x[0])
    
    # Min heap to track end times
    rooms = []
    heapq.heappush(rooms, intervals[0][1])
    
    for interval in intervals[1:]:
        # If meeting can use existing room
        if rooms[0] <= interval[0]:
            heapq.heappop(rooms)
        
        # Add current meeting's end time
        heapq.heappush(rooms, interval[1])
    
    return len(rooms)
```

### 4. Insert Interval
```python
def insert_interval(intervals, newInterval):
    result = []
    i = 0
    n = len(intervals)
    
    # Add all intervals ending before newInterval
    while i < n and intervals[i][1] < newInterval[0]:
        result.append(intervals[i])
        i += 1
    
    # Merge overlapping intervals
    while i < n and intervals[i][0] <= newInterval[1]:
        newInterval[0] = min(newInterval[0], intervals[i][0])
        newInterval[1] = max(newInterval[1], intervals[i][1])
        i += 1
    
    result.append(newInterval)
    
    # Add remaining intervals
    while i < n:
        result.append(intervals[i])
        i += 1
    
    return result
```

### 5. Non-overlapping Intervals
```python
def erase_overlap_intervals(intervals):
    if not intervals:
        return 0
    
    # Sort by end time
    intervals.sort(key=lambda x: x[1])
    
    non_overlap = 1
    end = intervals[0][1]
    
    for i in range(1, len(intervals)):
        if intervals[i][0] >= end:
            non_overlap += 1
            end = intervals[i][1]
    
    return len(intervals) - non_overlap
```

## Common Techniques

### 1. Sweep Line Algorithm
```python
def sweep_line(intervals):
    events = []
    # Add start and end events
    for start, end in intervals:
        events.append((start, 1))   # 1 for start
        events.append((end, -1))    # -1 for end
    
    events.sort()  # Sort by time
    
    current = 0
    max_overlap = 0
    
    for time, count in events:
        current += count
        max_overlap = max(max_overlap, current)
    
    return max_overlap
```

### 2. Interval Tree
```python
class IntervalNode:
    def __init__(self, interval):
        self.interval = interval
        self.max_end = interval[1]
        self.left = None
        self.right = None

def insert_interval_tree(root, interval):
    if not root:
        return IntervalNode(interval)
    
    if interval[0] < root.interval[0]:
        root.left = insert_interval_tree(root.left, interval)
    else:
        root.right = insert_interval_tree(root.right, interval)
    
    root.max_end = max(root.max_end, interval[1])
    return root
```

## Edge Cases to Consider
1. Empty interval list
2. Single interval
3. All intervals same
4. No overlap
5. Complete overlap
6. Nested intervals
7. Adjacent intervals
8. Negative time values
9. Large time values
10. Duplicate intervals

## Common Pitfalls
1. Not sorting intervals
2. Incorrect overlap check
3. Not handling empty input
4. Modifying input array
5. Integer overflow
6. Wrong sorting criteria
7. Memory inefficiency
8. Not considering duplicates

## Practice Problems by Difficulty

### Easy
1. [Meeting Rooms](https://leetcode.com/problems/meeting-rooms/) (LC #252)
2. [Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/) (LC #986)
3. [Teemo Attacking](https://leetcode.com/problems/teemo-attacking/) (LC #495)

### Medium
1. [Merge Intervals](https://leetcode.com/problems/merge-intervals/) (LC #56)
2. [Insert Interval](https://leetcode.com/problems/insert-interval/) (LC #57)
3. [Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/) (LC #253)
4. [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/) (LC #435)

### Hard
1. [Employee Free Time](https://leetcode.com/problems/employee-free-time/) (LC #759)
2. [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) (LC #452)
3. [Data Stream as Disjoint Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/) (LC #352)

## Real-World Applications
1. **Calendar Systems**:
   - Meeting scheduling
   - Resource booking
2. **Resource Management**:
   - CPU scheduling
   - Memory allocation
3. **Network Management**:
   - Bandwidth allocation
   - Traffic scheduling
4. **Project Planning**:
   - Task scheduling
   - Timeline management
5. **Database Systems**:
   - Transaction scheduling
   - Lock management
6. **Transportation**:
   - Flight scheduling
   - Vehicle routing

## Advanced Topics
1. **Interval Trees**:
   - Construction
   - Query optimization
2. **Segment Trees**:
   - Range queries
   - Lazy propagation
3. **Line Sweep Algorithms**:
   - Event processing
   - Geometric applications
4. **Dynamic Intervals**:
   - Online algorithms
   - Real-time updates

## Important Resources
1. [Interval Scheduling Algorithms](https://www.cs.princeton.edu/~wayne/kleinberg-tardos/pdf/04GreedyAlgorithmsI.pdf)
2. [Sweep Line Technique](https://www.topcoder.com/thrive/articles/Line%20Sweep%20Algorithms)
3. [Interval Tree Tutorial](https://www.geeksforgeeks.org/interval-tree/)
4. [Meeting Room Problems](https://leetcode.com/problems/meeting-rooms-ii/solution/)
5. [Segment Tree Applications](https://cp-algorithms.com/data_structures/segment_tree.html)

## Interview Tips
1. Clarify interval representation
2. Consider sorting strategy
3. Handle edge cases explicitly
4. Draw timeline diagrams
5. Consider optimization opportunities
6. Test with small examples
7. Analyze time/space complexity
8. Consider follow-up questions
9. Discuss trade-offs
10. Think about scalability