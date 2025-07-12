# Tree Data Structure 🌲

## Introduction
A tree is a hierarchical data structure composed of nodes connected by edges. Each node contains a value and references to its child nodes. Trees are widely used for representing hierarchical relationships and optimizing search operations.

## Core Concepts

### Important Terminologies
- **Node**: Basic unit containing data and references to children
- **Root**: Top node of the tree
- **Leaf**: Node with no children
- **Internal Node**: Node with at least one child
- **Parent/Child**: Relationship between connected nodes
- **Ancestor/Descendant**: Nodes in path to root/leaves
- **Height**: Length of path from node to deepest leaf
- **Depth**: Length of path from node to root
- **Level**: Number of edges from root to node
- **Balanced Tree**: Height difference of subtrees ≤ 1
- **Binary Tree**: Each node has at most 2 children
- **Binary Search Tree (BST)**: Left subtree < node < right subtree
- **Complete Tree**: All levels filled except possibly last
- **Perfect Tree**: All levels completely filled

### Time Complexity Analysis
| Operation     | Average (BST) | Worst (BST) | Balanced BST |
|--------------|---------------|-------------|--------------|
| Search       | O(log n)      | O(n)        | O(log n)     |
| Insert       | O(log n)      | O(n)        | O(log n)     |
| Delete       | O(log n)      | O(n)        | O(log n)     |
| Traversal    | O(n)          | O(n)        | O(n)         |
| Height       | O(log n)      | O(n)        | O(log n)     |

### Space Complexity
- **Perfect Binary Tree**: O(2^h) where h is height
- **Balanced Binary Tree**: O(n) where n is number of nodes
- **Skewed Tree**: O(n) but behaves like linked list

## Implementation

### Basic Tree Node
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

### Binary Search Tree Implementation
```python
class BST:
    def __init__(self):
        self.root = None
    
    def insert(self, val):
        if not self.root:
            self.root = TreeNode(val)
            return
        
        curr = self.root
        while True:
            if val < curr.val:
                if not curr.left:
                    curr.left = TreeNode(val)
                    break
                curr = curr.left
            else:
                if not curr.right:
                    curr.right = TreeNode(val)
                    break
                curr = curr.right
    
    def search(self, val):
        curr = self.root
        while curr and curr.val != val:
            curr = curr.left if val < curr.val else curr.right
        return curr
```

## Tree Traversal Techniques

### 1. Depth-First Search (DFS)
```python
def inorder(root):  # Left -> Root -> Right
    if not root:
        return []
    return inorder(root.left) + [root.val] + inorder(root.right)

def preorder(root):  # Root -> Left -> Right
    if not root:
        return []
    return [root.val] + preorder(root.left) + preorder(root.right)

def postorder(root):  # Left -> Right -> Root
    if not root:
        return []
    return postorder(root.left) + postorder(root.right) + [root.val]
```

### 2. Breadth-First Search (BFS)
```python
from collections import deque

def level_order(root):
    if not root:
        return []
    
    result = []
    queue = deque([root])
    
    while queue:
        level = []
        level_size = len(queue)
        
        for _ in range(level_size):
            node = queue.popleft()
            level.append(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(level)
    
    return result
```

## Common Techniques

### 1. Lowest Common Ancestor (LCA)
```python
def lowest_common_ancestor(root, p, q):
    if not root or root == p or root == q:
        return root
    
    left = lowest_common_ancestor(root.left, p, q)
    right = lowest_common_ancestor(root.right, p, q)
    
    if left and right:
        return root
    return left if left else right
```

### 2. Path Sum
```python
def has_path_sum(root, target_sum):
    if not root:
        return False
    
    if not root.left and not root.right:
        return root.val == target_sum
    
    return (has_path_sum(root.left, target_sum - root.val) or
            has_path_sum(root.right, target_sum - root.val))
```

### 3. Tree Validation
```python
def is_valid_bst(root, min_val=float('-inf'), max_val=float('inf')):
    if not root:
        return True
    
    if root.val <= min_val or root.val >= max_val:
        return False
    
    return (is_valid_bst(root.left, min_val, root.val) and
            is_valid_bst(root.right, root.val, max_val))
```

## Edge Cases to Consider
1. Empty tree
2. Single node tree
3. Complete binary tree
4. Perfect binary tree
5. Skewed tree (left/right)
6. Duplicate values
7. Negative values
8. Maximum/minimum values
9. Unbalanced tree
10. Tree with cycles (invalid)

## Common Pitfalls
1. Not handling null nodes
2. Incorrect recursion base cases
3. Stack overflow in deep trees
4. Not considering duplicates
5. Assuming balanced tree
6. Incorrect BST validation
7. Memory leaks in deletion

## Practice Problems by Difficulty

### Easy
1. [Same Tree](https://leetcode.com/problems/same-tree/) (LC #100)
2. [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) (LC #104)
3. [Path Sum](https://leetcode.com/problems/path-sum/) (LC #112)
4. [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) (LC #226)

### Medium
1. [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) (LC #102)
2. [Construct Binary Tree from Preorder and Inorder](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) (LC #105)
3. [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) (LC #103)
4. [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) (LC #98)

### Hard
1. [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) (LC #124)
2. [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/) (LC #297)
3. [Binary Tree Cameras](https://leetcode.com/problems/binary-tree-cameras/) (LC #968)

## Real-World Applications
1. **File Systems**: Directory structure
2. **HTML DOM**: Web page structure
3. **Database Indexing**: B-trees and variants
4. **Compiler Design**: Abstract syntax trees
5. **Network Routing**: Routing tables
6. **AI/Game Theory**: Decision trees
7. **Compression**: Huffman coding

## Advanced Topics
1. **Self-Balancing Trees**:
   - AVL Trees
   - Red-Black Trees
   - B-Trees
2. **Segment Trees**: Range queries
3. **Fenwick Trees**: Prefix sums
4. **Threaded Binary Trees**
5. **Splay Trees**
6. **Trie (Prefix Trees)**

## Important Resources
1. [Tree Traversals](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)
2. [Binary Search Tree](https://www.programiz.com/dsa/binary-search-tree)
3. [AVL Tree Tutorial](https://www.geeksforgeeks.org/avl-tree-set-1-insertion/)
4. [Red-Black Tree Guide](https://www.geeksforgeeks.org/red-black-tree-set-1-introduction-2/)
5. [B-Tree and B+ Tree](https://www.geeksforgeeks.org/introduction-of-b-tree-2/)

## Interview Tips
1. Clarify tree type and properties
2. Consider recursive vs iterative approaches
3. Analyze space complexity (recursion stack)
4. Handle edge cases explicitly
5. Use helper functions for complex logic
6. Consider in-place vs new tree solutions
7. Test with small examples first
8. Draw the tree for visualization