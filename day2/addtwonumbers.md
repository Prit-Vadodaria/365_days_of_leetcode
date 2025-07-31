# ➕ Add Two Numbers – C++ Linked List Solution

## 📝 Problem Statement

You are given **two non-empty linked lists** representing two non-negative integers. The digits are stored in **reverse order**, and each node contains a **single digit**. Add the two numbers and return the sum as a linked list.

- The two numbers **do not contain any leading zero**, except for the number `0` itself.
- The result should also be returned as a **linked list in reverse order**.

---

## 📥 Input / 📤 Output

### Input
- Two singly-linked lists `l1` and `l2`.

### Output
- A singly-linked list representing the sum of the two numbers in reverse order.

---

## 💡 Example

### Example 1:
Input: l1 = [2, 4, 3], l2 = [5, 6, 4]
Output: [7, 0, 8]
Explanation: 342 + 465 = 807

### Example 2:
Input: l1 = [0], l2 = [0]
Output: [0]

### Example 3:
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
Explanation: 9999999 + 9999 = 10009998


---

## 🚀 Approach

### 🧠 Idea
To simulate manual addition:
- Traverse both linked lists node by node.
- Add corresponding digits along with any carry from the previous addition.
- Store the sum's **units digit** in a new node and carry over the **tens digit**.

### 🪜 Steps
1. Use a **dummy node** to simplify edge case handling.
2. Traverse both lists using a while loop until both are null and no carry remains.
3. For each step:
   - Extract current digits (or use `0` if the node is null).
   - Compute `sum = val1 + val2 + carry`.
   - Update `carry = sum / 10`.
   - Append a new node with `sum % 10` to the result list.
4. Return `dummy->next` as the head of the result list.

---

## 📌 C++ Implementation

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode(0);
        ListNode* current = dummy;
        int carry = 0;

        while (l1 != nullptr || l2 != nullptr || carry != 0) {
            int val1 = (l1 != nullptr) ? l1->val : 0;
            int val2 = (l2 != nullptr) ? l2->val : 0;
            int sum = val1 + val2 + carry;
            carry = sum / 10;

            current->next = new ListNode(sum % 10);
            current = current->next;

            if (l1 != nullptr) l1 = l1->next;
            if (l2 != nullptr) l2 = l2->next;
        }

        return dummy->next;
    }
};
```
