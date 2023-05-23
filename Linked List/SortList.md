<h1> Merge Sort : </h1> 

```
    ListNode* sortedMerge(ListNode* head1, ListNode* head2)  {  
        ListNode* finalHead = NULL;
        ListNode* finalTail = NULL;
        if (head1 == NULL) return head2;
        if (head2 == NULL) return head1;
        while (head1 && head2) {
            if (finalHead == NULL && finalTail == NULL) {
                if (head1-> val > head2-> val) {
                    finalHead = head2;
                    finalTail = head2;
                    head2 = head2->next;
                } else {
                    finalHead = head1;
                    finalTail = head1;
                    head1 = head1->next;
                }
            }   
            if (head1 && head2 && head1-> val < head2-> val) {
                finalTail->next = head1;
                finalTail = finalTail->next;
                head1 = head1->next;
            } else if (head1 && head2 && head1-> val >= head2-> val) {
                finalTail->next = head2;
                finalTail = finalTail->next;
                head2 = head2->next;
            }
        }     
        while (head1) {
            finalTail->next = head1;
            finalTail = finalTail->next;
            head1 = head1->next;
        }
        while (head2) {
            finalTail->next = head2;
            finalTail = finalTail->next;
            head2 = head2->next;
        }
        return finalHead;
    }
    ListNode* sortList(ListNode* head) {
        if(head == NULL || head ->next == NULL) return head;
        ListNode *temp = NULL;
        ListNode *slow = head;
        ListNode *fast = head;
        //middle of linked list
        while(fast !=  NULL && fast -> next != NULL){
            temp = slow;
            slow = slow->next;          
            fast = fast ->next ->next;  
        }   
        temp -> next = NULL;       
        ListNode* l1 = sortList(head);
        ListNode* l2 = sortList(slow);
        return sortedMerge(l1, l2); 
    }
};
