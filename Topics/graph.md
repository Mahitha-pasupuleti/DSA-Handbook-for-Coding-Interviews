# Graph Data Structure and Algorithms 🌐

## Introduction
A graph is a non-linear data structure consisting of vertices (nodes) and edges that connect these vertices. Graphs are used to represent networks, relationships, and various real-world problems from social networks to computer networks.

## Core Concepts

### Important Terminologies
- **Vertex/Node**: Basic unit of a graph
- **Edge**: Connection between two vertices
- **Directed Graph**: Edges have direction
- **Undirected Graph**: Edges are bidirectional
- **Weighted Graph**: Edges have weights/costs
- **Path**: Sequence of vertices connected by edges
- **Cycle**: Path that starts and ends at same vertex
- **DAG**: Directed Acyclic Graph (no cycles)
- **Connected Component**: Subset of connected vertices
- **Degree**: Number of edges connected to a vertex
- **Tree**: Connected graph with no cycles
- **Bipartite Graph**: Vertices can be split into two sets
- **Strongly Connected**: Every vertex reachable from every other
- **Adjacency**: Direct connection between vertices

### Graph Representations
1. **Adjacency Matrix**:
   - 2D array where matrix[i][j] represents edge from i to j
   - Space: O(V²)
   - Good for dense graphs

2. **Adjacency List**:
   - Array of lists where list[i] contains vertices adjacent to i
   - Space: O(V + E)
   - Good for sparse graphs

3. **Edge List**:
   - List of all edges in graph
   - Space: O(E)
   - Good for algorithms that process all edges

### Time Complexity Analysis
| Operation           | Adjacency List | Adjacency Matrix |
|--------------------|----------------|------------------|
| Add Vertex         | O(1)           | O(V²)            |
| Add Edge           | O(1)           | O(1)             |
| Remove Vertex      | O(V + E)       | O(V²)            |
| Remove Edge        | O(E)           | O(1)             |
| Query Edge         | O(V)           | O(1)             |
| Find Neighbors     | O(V)           | O(V)             |
| Storage Space      | O(V + E)       | O(V²)            |

## Implementation

### Basic Graph using Adjacency List
```python
class Graph:
    def __init__(self, directed=False):
        self.graph = {}
        self.directed = directed
    
    def add_vertex(self, vertex):
        if vertex not in self.graph:
            self.graph[vertex] = []
    
    def add_edge(self, v1, v2):
        if v1 not in self.graph:
            self.add_vertex(v1)
        if v2 not in self.graph:
            self.add_vertex(v2)
        
        self.graph[v1].append(v2)
        if not self.directed:
            self.graph[v2].append(v1)
    
    def get_vertices(self):
        return list(self.graph.keys())
    
    def get_edges(self):
        edges = []
        for vertex in self.graph:
            for neighbor in self.graph[vertex]:
                if not self.directed and (neighbor, vertex) not in edges:
                    edges.append((vertex, neighbor))
                else:
                    edges.append((vertex, neighbor))
        return edges
```

### Weighted Graph Implementation
```python
class WeightedGraph:
    def __init__(self, directed=False):
        self.graph = {}
        self.directed = directed
    
    def add_vertex(self, vertex):
        if vertex not in self.graph:
            self.graph[vertex] = {}
    
    def add_edge(self, v1, v2, weight):
        if v1 not in self.graph:
            self.add_vertex(v1)
        if v2 not in self.graph:
            self.add_vertex(v2)
        
        self.graph[v1][v2] = weight
        if not self.directed:
            self.graph[v2][v1] = weight
```

## Common Algorithms

### 1. Depth-First Search (DFS)
```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(start)
    print(start, end=' ')
    
    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
```

### 2. Breadth-First Search (BFS)
```python
from collections import deque

def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    
    while queue:
        vertex = queue.popleft()
        print(vertex, end=' ')
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### 3. Dijkstra's Shortest Path
```python
import heapq

def dijkstra(graph, start):
    distances = {vertex: float('infinity') for vertex in graph}
    distances[start] = 0
    pq = [(0, start)]
    
    while pq:
        current_distance, current_vertex = heapq.heappop(pq)
        
        if current_distance > distances[current_vertex]:
            continue
        
        for neighbor, weight in graph[current_vertex].items():
            distance = current_distance + weight
            
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(pq, (distance, neighbor))
    
    return distances
```

### 4. Topological Sort
```python
def topological_sort(graph):
    visited = set()
    stack = []
    
    def dfs(vertex):
        visited.add(vertex)
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                dfs(neighbor)
        
        stack.append(vertex)
    
    for vertex in graph:
        if vertex not in visited:
            dfs(vertex)
    
    return stack[::-1]
```

### 5. Union-Find (Disjoint Set)
```python
class UnionFind:
    def __init__(self, vertices):
        self.parent = {v: v for v in vertices}
        self.rank = {v: 0 for v in vertices}
    
    def find(self, item):
        if self.parent[item] != item:
            self.parent[item] = self.find(self.parent[item])
        return self.parent[item]
    
    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)
        
        if rootX != rootY:
            if self.rank[rootX] < self.rank[rootY]:
                rootX, rootY = rootY, rootX
            self.parent[rootY] = rootX
            if self.rank[rootX] == self.rank[rootY]:
                self.rank[rootX] += 1
```

## Common Patterns

### 1. Cycle Detection
```python
def has_cycle(graph):
    visited = set()
    rec_stack = set()
    
    def dfs(vertex):
        visited.add(vertex)
        rec_stack.add(vertex)
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                if dfs(neighbor):
                    return True
            elif neighbor in rec_stack:
                return True
        
        rec_stack.remove(vertex)
        return False
    
    for vertex in graph:
        if vertex not in visited:
            if dfs(vertex):
                return True
    return False
```

### 2. Connected Components
```python
def find_connected_components(graph):
    visited = set()
    components = []
    
    def dfs(vertex, component):
        visited.add(vertex)
        component.append(vertex)
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                dfs(neighbor, component)
    
    for vertex in graph:
        if vertex not in visited:
            component = []
            dfs(vertex, component)
            components.append(component)
    
    return components
```

## Edge Cases to Consider
1. Empty graph
2. Single vertex
3. Disconnected components
4. Self-loops
5. Parallel edges
6. Negative weights
7. Cycles
8. Dense vs sparse graphs
9. Directed vs undirected
10. Bipartite properties

## Common Pitfalls
1. Not handling disconnected components
2. Incorrect cycle detection
3. Stack overflow in DFS
4. Not considering edge weights
5. Assuming undirected graph
6. Memory issues with adjacency matrix
7. Not handling self-loops

## Practice Problems by Difficulty

### Easy
1. [Find the Town Judge](https://leetcode.com/problems/find-the-town-judge/) (LC #997)
2. [Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/) (LC #1791)
3. [Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC #200)

### Medium
1. [Course Schedule](https://leetcode.com/problems/course-schedule/) (LC #207)
2. [Clone Graph](https://leetcode.com/problems/clone-graph/) (LC #133)
3. [Redundant Connection](https://leetcode.com/problems/redundant-connection/) (LC #684)
4. [Network Delay Time](https://leetcode.com/problems/network-delay-time/) (LC #743)

### Hard
1. [Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/) (LC #1192)
2. [Word Ladder](https://leetcode.com/problems/word-ladder/) (LC #127)
3. [Bus Routes](https://leetcode.com/problems/bus-routes/) (LC #815)

## Real-World Applications
1. **Social Networks**: Friend connections
2. **Computer Networks**: Network topology
3. **GPS Navigation**: Road networks
4. **Recommendation Systems**: User-item relationships
5. **Compiler Design**: Control flow analysis
6. **Biology**: Protein interaction networks
7. **Circuit Design**: Electronic circuits

## Advanced Topics
1. **Advanced Graph Algorithms**:
   - A* Search
   - Bellman-Ford
   - Floyd-Warshall
2. **Network Flow**:
   - Ford-Fulkerson
   - Max-Flow Min-Cut
3. **Graph Coloring**:
   - Vertex coloring
   - Edge coloring
4. **Planar Graphs**
5. **Graph Isomorphism**
6. **Spectral Graph Theory**

## Important Resources
1. [Graph Theory Basics](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)
2. [Network Flow Tutorial](https://www.geeksforgeeks.org/max-flow-problem-introduction/)
3. [Advanced Graph Algorithms](https://cp-algorithms.com/graph/basic-graph.html)
4. [Graph Applications](https://www.geeksforgeeks.org/applications-of-graph-data-structure/)
5. [Graph Visualization Tools](https://graphviz.org/)

## Interview Tips
1. Clarify graph properties
2. Choose appropriate representation
3. Consider time/space complexity
4. Handle edge cases explicitly
5. Draw examples
6. Consider optimization opportunities
7. Test with small graphs first
8. Discuss trade-offs