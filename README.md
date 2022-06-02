# RemoveduplicatesLinkedlist
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
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while(curr && curr->next){
            if(curr->val==curr->next->val){
                while(curr->next && curr->val==curr->next->val)
                    curr = curr->next;
                if(!prev)
                    head = curr->next;
                else
                    prev->next = curr->next;
            }
            else{
                if(!prev)
                    prev = curr;
                else
                    prev = prev->next;
            }
            curr = curr->next;
        }
        return head;
    }
};
