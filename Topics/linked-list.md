# Topic Name: 🔗 Linked List

### Important Terminologies:
- Singly Linked List: Nodes with single pointer.
- Doubly Linked List: Nodes with next and prev pointers.
- Circular Linked List: Last node points to first node.

### Time Complexity:
- Traversal: O(n)
- Insertion/Deletion at head: O(1)
- Searching: O(n)

### Less Known but Important Points:
- Use dummy nodes to simplify edge cases.
- Linked lists have poor cache locality compared to arrays.
- Detect cycles using Floyd’s Tortoise and Hare.

### Edge Cases to Consider:
- Empty list.
- Single node list.
- Cycle presence.

### Common Coding Interview Patterns:
- Two pointers (fast and slow).
- Reverse linked list.
- Merge k sorted lists (using heap).

### Relevant LeetCode Problems:
- [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (LC #206)
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) (LC #141)
- [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC #23)

### Links to Important Resources:
- [Floyd’s Cycle Detection](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)
- [Linked List Introduction](https://www.geeksforgeeks.org/data-structures/linked-list/)
- [Dummy Node Usage](https://leetcode.com/problems/remove-nth-node-from-end-of-list/solution/)