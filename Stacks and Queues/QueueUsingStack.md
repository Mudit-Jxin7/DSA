![image](https://github.com/Mudit-Jxin7/DSA/assets/97677133/dfd57f2c-a994-4a72-839a-92805ed07e36)
```
class MyQueue {
    stack <int> s1;
    stack <int> s2;
public:
    MyQueue() {
        
    }
    
    void push(int x) {
        while(!s1.empty()){
            int top = s1.top();
            s1.pop();
            s2.push(top);
        }

        s1.push(x);

        while(!s2.empty()){
            int top = s2.top();
            s2.pop();
            s1.push(top);
        }
    }
    
    int pop() {
        int top = s1.top();
        s1.pop();
        return top;
    }
    
    int peek() {
        return s1.top();
    }
    
    bool empty() {
        return s1.empty();
    }
};
