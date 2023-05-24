```
class Solution {
public:
    Node* copyRandomList(Node* head) {
        //1st Step : Create Copy Nodes between original list
        Node *temp = head;
        Node *front = head;
        while(temp){
            Node *node = new Node(temp -> val);
            front = temp -> next;
            temp -> next = node;
            node -> next = front;
            temp = front;
        }

        //2nd Step : Assign random pointers 
        temp = head;
        while(temp){
            if(temp -> random != NULL) temp -> next -> random = temp -> random -> next;
            temp = temp -> next -> next;
        }

        //3rd Extract the cloned list from original list
        Node *dummy = new Node(0);
        Node *res = dummy;
        temp = head;
        front = head;

        while(temp){
            front = temp -> next -> next;
            res -> next = temp -> next;
            temp -> next = front;
            res = res -> next;
            temp = front;
        }

        return dummy -> next;
    }
};
