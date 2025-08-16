# Remove Duplicates from Sorted List

This project contains a C++ solution for the LeetCode problem **"Remove Duplicates from Sorted List" (Problem #83)**.

## Problem Statement
Given the head of a sorted linked list, delete all duplicates such that each element appears only once.  
Return the linked list sorted as well.

### Example 1
**Input:**
```
head = [1,1,2]
```
**Output:**
```
[1,2]
```

### Example 2
**Input:**
```
head = [1,1,2,3,3]
```
**Output:**
```
[1,2,3]
```

---

## Constraints
- The number of nodes in the list is in the range `[0, 300]`.
- `-100 <= Node.val <= 100`
- The list is guaranteed to be sorted in ascending order.

---

## C++ Solution

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head) return nullptr;  

        ListNode* tp = head;
        while (tp->next != nullptr) {
            if (tp->next->val == tp->val) {
                ListNode* todel = tp->next;
                tp->next = todel->next; // skip duplicate
            } else {
                tp = tp->next; // move to next unique node
            }
        }
        return head;
    }
};
```

---

## Explanation
- Traverse the linked list using a pointer `tp`.
- While `tp->next` exists:
  - If `tp->next->val == tp->val`, we found a duplicate → remove it by skipping the node.
  - Otherwise, move `tp` forward.
- This ensures each element appears only once in the final list.

---

## Complexity Analysis
- **Time Complexity:** `O(n)` → we traverse the list once.
- **Space Complexity:** `O(1)` → we use only a pointer.
