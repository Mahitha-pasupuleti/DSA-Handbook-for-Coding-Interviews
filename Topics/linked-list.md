# Linked List Data Structure 🔗

## Introduction
A linked list is a linear data structure where elements are stored in nodes, and each node points to the next node in the sequence. Unlike arrays, linked lists don't require contiguous memory allocation.

## Core Concepts

### Important Terminologies
- **Node**: Basic unit containing data and pointer(s)
- **Head**: First node of the linked list
- **Tail**: Last node of the linked list
- **Singly Linked List**: Each node has one pointer to next node
- **Doubly Linked List**: Each node has pointers to next and previous nodes
- **Circular Linked List**: Last node points back to first node
- **Dummy Node**: Extra node used to handle edge cases

### Time Complexity Analysis
| Operation           | Singly Linked | Doubly Linked |
|--------------------|---------------|---------------|
| Access             | O(n)          | O(n)          |
| Search             | O(n)          | O(n)          |
| Insert at Head     | O(1)          | O(1)          |
| Insert at Tail     | O(1)*         | O(1)          |
| Delete at Head     | O(1)          | O(1)          |
| Delete at Tail     | O(n)          | O(1)          |
| Insert at Position | O(n)          | O(n)          |
| Delete at Position | O(n)          | O(n)          |

*O(1) if we maintain tail pointer

### Space Complexity
- **Singly Linked**: O(n) with 1 pointer per node
- **Doubly Linked**: O(n) with 2 pointers per node
- **Memory Overhead**: Higher than arrays due to pointers

## Implementation

### Singly Linked List
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class SinglyLinkedList:
    def __init__(self):
        self.head = None
        self.size = 0
    
    def insert_at_head(self, val):
        new_node = ListNode(val)
        new_node.next = self.head
        self.head = new_node
        self.size += 1
    
    def delete_at_head(self):
        if not self.head:
            return None
        val = self.head.val
        self.head = self.head.next
        self.size -= 1
        return val
    
    def get_size(self):
        return self.size
```

### Doubly Linked List
```python
class DoublyListNode:
    def __init__(self, val=0, next=None, prev=None):
        self.val = val
        self.next = next
        self.prev = prev

class DoublyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None
        self.size = 0
    
    def insert_at_head(self, val):
        new_node = DoublyListNode(val)
        if not self.head:
            self.head = self.tail = new_node
        else:
            new_node.next = self.head
            self.head.prev = new_node
            self.head = new_node
        self.size += 1
    
    def insert_at_tail(self, val):
        new_node = DoublyListNode(val)
        if not self.tail:
            self.head = self.tail = new_node
        else:
            new_node.prev = self.tail
            self.tail.next = new_node
            self.tail = new_node
        self.size += 1
```

## Common Techniques

### 1. Floyd's Cycle Detection (Tortoise and Hare)
```python
def has_cycle(head):
    if not head or not head.next:
        return False
    
    slow = head
    fast = head.next
    
    while slow != fast:
        if not fast or not fast.next:
            return False
        slow = slow.next
        fast = fast.next.next
    
    return True
```

### 2. Reverse Linked List
```python
def reverse_list(head):
    prev = None
    curr = head
    
    while curr:
        next_temp = curr.next
        curr.next = prev
        prev = curr
        curr = next_temp
    
    return prev
```

### 3. Merge Two Sorted Lists
```python
def merge_two_lists(l1, l2):
    dummy = ListNode(0)
    curr = dummy
    
    while l1 and l2:
        if l1.val <= l2.val:
            curr.next = l1
            l1 = l1.next
        else:
            curr.next = l2
            l2 = l2.next
        curr = curr.next
    
    curr.next = l1 if l1 else l2
    return dummy.next
```

## Common Patterns

### 1. Two Pointer Technique
- Fast & Slow pointers (Floyd's algorithm)
- Multiple passes with offset
- Parallel traversal

### 2. Dummy Node Pattern
```python
def remove_nth_from_end(head, n):
    dummy = ListNode(0)
    dummy.next = head
    first = dummy
    second = dummy
    
    # Advance first pointer by n+1 steps
    for i in range(n + 1):
        first = first.next
    
    # Move both pointers until first reaches end
    while first:
        first = first.next
        second = second.next
    
    # Remove nth node
    second.next = second.next.next
    return dummy.next
```

## Edge Cases to Consider
1. Empty list
2. Single node list
3. Two node list
4. Circular list
5. List with cycles
6. Operations at head/tail
7. Duplicate values
8. Multiple cycles

## Common Pitfalls
1. Not handling null pointers
2. Memory leaks in deletion
3. Losing the head reference
4. Incorrect cycle detection
5. Off-by-one errors in counting
6. Not updating tail pointer

## Practice Problems by Difficulty

### Easy
1. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (LC #206)
2. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) (LC #141)
3. [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/) (LC #234)
4. [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) (LC #876)

### Medium
1. [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) (LC #2)
2. [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) (LC #19)
3. [Rotate List](https://leetcode.com/problems/rotate-list/) (LC #61)
4. [Sort List](https://leetcode.com/problems/sort-list/) (LC #148)

### Hard
1. [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC #23)
2. [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) (LC #25)
3. [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) (LC #138)

## Real-World Applications
1. **Memory Management**: Implementation of free lists
2. **Undo Systems**: History tracking in editors
3. **Hash Tables**: Collision resolution using chaining
4. **File Systems**: Directory implementations
5. **Music Player**: Playlist implementation

## Advanced Topics
1. **Skip Lists**: Probabilistic alternative to balanced trees
2. **XOR Linked Lists**: Memory-efficient doubly linked lists
3. **Self-Organizing Lists**: 
   - Move to Front
   - Transpose
   - Count
4. **Concurrent Linked Lists**:
   - Lock-free implementations
   - Wait-free implementations

## Important Resources
1. [Floyd's Cycle Detection Algorithm](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)
2. [Linked List Data Structure](https://www.geeksforgeeks.org/data-structures/linked-list/)
3. [Skip Lists Tutorial](https://www.geeksforgeeks.org/skip-list/)
4. [XOR Linked List](https://www.geeksforgeeks.org/xor-linked-list-a-memory-efficient-doubly-linked-list-set-1/)
5. [Self-Organizing Lists](https://www.geeksforgeeks.org/self-organizing-list-set-1-introduction/)

## Interview Tips
1. Always validate input parameters
2. Consider memory management
3. Handle edge cases explicitly
4. Use dummy nodes when helpful
5. Draw pointer manipulations
6. Test with small examples first
7. Consider maintaining tail pointer