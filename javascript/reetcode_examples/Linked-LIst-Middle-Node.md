# Code Principles Used
- **Two Pointers**: Using a slow pointer and a fast pointer to traverse the list at different speeds.
- **Singly Linked List Traversal**: Iterating through the linked list by moving the `next` pointer.
- **Efficiency**: The two-pointer approach ensures that the middle is found in a single traversal (O(n) time complexity).

## Find the Middle Node of a Linked List
### Problem Summary
Given the head of a singly linked list, return the middle node. If the list contains an even number of nodes, return the second middle node. This is achieved by moving one pointer twice as fast as the other. When the fast pointer reaches the end of the list, the slow pointer will point to the middle.

### Code
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val === undefined ? 0 : val);
 *     this.next = (next === undefined ? null : next);
 * }
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
const middleNode = function(head) {
    let slow = head; // Moves one step at a time
    let fast = head; // Moves two steps at a time

    // Traverse the list with the two pointers
    while (fast !== null && fast.next !== null) {
        slow = slow.next; // Slow pointer moves one step
        fast = fast.next.next; // Fast pointer moves two steps
    }

    // When fast reaches the end, slow is at the middle
    return slow;
};
```

### Explanation of Code
1. **Initialize Two Pointers**: 
   - `slow` starts at the head and moves one node at a time.
   - `fast` also starts at the head but moves two nodes at a time.
2. **Traverse the List**:
   - In each iteration of the `while` loop:
     - Move `slow` one step forward using `slow.next`.
     - Move `fast` two steps forward using `fast.next.next`.
   - The loop continues until `fast` reaches the end of the list or there are no more nodes to process (`fast.next` is `null`).
3. **Return the Middle Node**:
   - When the loop exits, `slow` will point to the middle node because it has traversed half the distance of `fast`.

This approach is efficient (O(n) time complexity and O(1) space complexity) and does not require storing additional information about the list's length.