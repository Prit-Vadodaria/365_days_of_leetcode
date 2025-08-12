# Remove Nth Node From End of List

## Problem Statement

Given the head of a linked list, remove the nth node from the end of the list and return its head.

### Example 1:
**Input:** head = [1,2,3,4,5], n = 2  
**Output:** [1,2,3,5]  

### Example 2:
**Input:** head = [1], n = 1  
**Output:** []  

### Example 3:
**Input:** head = [1,2], n = 1  
**Output:** [1]  

## Constraints:
- The number of nodes in the list is `sz`.
- 1 <= sz <= 30
- 0 <= Node.val <= 100
- 1 <= n <= sz

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
    int size(ListNode* head)
    {
        int sz=0;
        ListNode* tp= head;
        while(tp!= NULL)
        {
            tp=tp->next;
            sz++;
        }
        return sz;
    }
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int sz=size(head);
        int prev_ith_element=sz-n;
        ListNode* tp=head;
        if(prev_ith_element==0)
        {
            ListNode* node_to_del=tp;
            head=node_to_del->next;
            delete node_to_del;
            return head;
        }
        for(int  i=0;i<prev_ith_element-1;i++)
        {
            tp=tp->next;
        }
        ListNode* node_to_del=tp->next;
        if(node_to_del==NULL)
        {
            delete node_to_del;
            return head;
        }
        tp->next=node_to_del->next;
        delete node_to_del;
        return head;
    }
};
```

---

## Explanation

1. **Find Size:** A helper function `size()` counts the total number of nodes in the linked list.
2. **Locate Node to Remove:** We calculate the position of the node before the target node (`prev_ith_element = size - n`).
3. **Edge Case:** If removing the first node, update `head` to the next node.
4. **Delete Node:** Adjust pointers and free memory.

---

## Complexity Analysis

- **Time Complexity:** O(sz) — We traverse the list twice: once for size calculation and once to find the node.
- **Space Complexity:** O(1) — No extra space is used apart from variables.
