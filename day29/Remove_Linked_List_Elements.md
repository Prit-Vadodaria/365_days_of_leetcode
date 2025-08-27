# 🧩 Remove Linked List Elements

## Problem Statement

Given the head of a linked list and an integer `val`, remove all the nodes of the linked list that have `Node.val == val`, and return the new head.

---

## Examples

**Example 1:**
```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

**Example 2:**
```
Input: head = [], val = 1
Output: []
```

**Example 3:**
```
Input: head = [7,7,7,7], val = 7
Output: []
```

---

## Constraints
- The number of nodes in the list is in the range `[0, 10^4]`.
- `1 <= Node.val <= 50`
- `0 <= val <= 50`

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
    ListNode* removeElements(ListNode* head, int val) {
        if(!head)
        {
            return head;
        }        
        while(head && head->val == val)
        {   
            ListNode* todel = head;
            head = head->next;
        }
        ListNode* prev = head;
        if(!prev) return NULL;
        ListNode* tp = head->next;
        while(tp)
        {
            if(tp->val == val)
            {
                ListNode* todel = tp;
                prev->next = todel->next;
                tp = prev->next;
            }
            else
            {
                prev = tp;
                tp = tp->next;
            }
        }
        return head;
    }
};
```

---

✅ This solution iterates through the list, skipping nodes equal to `val` at the start, then traverses with two pointers (`prev` and `tp`) to unlink nodes that match the target value.
