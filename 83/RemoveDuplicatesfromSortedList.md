```C++
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(head == NULL) return nullptr;
        ListNode* cur = head;
        while (head->next) {
            if (cur->next->val == cur->val) {
                cur->next = cur->next->next;
            }
            else cur = cur->next;
        }
        return head;
    }
};
```
