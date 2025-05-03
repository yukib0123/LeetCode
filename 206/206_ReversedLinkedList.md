```C++
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
    ListNode* reverseList(ListNode* head) {
        stack<int> st;
        while (head){
            st.push(head->val);
            head = head->next;
        }
        if (st.empty()) return nullptr;
        ListNode* reversedhead = new ListNode(st.top());
        st.pop();
        ListNode* newcur = reversedhead;
        while (!st.empty()) {
            newcur->next = new ListNode(st.top());
            st.pop();
            newcur = newcur->next;
        }
        return reversedhead;
    }
};
```
