Approach 1 : two queues


![image](https://github.com/Mudit-Jxin7/DSA/assets/97677133/c1506763-0401-40c8-b1c8-913097133777)

```
class MyStack {
    queue <int> q1;
    queue <int> q2;
public:
    MyStack() {
        
    }
    
    void push(int x) {
        q2.push(x);
        while(!q1.empty()){
            int top = q1.front();
            q1.pop();
            q2.push(top);
        }

        swap(q1 , q2);
    }
    
    int pop() {
        int num = q1.front();
        q1.pop();
        return num;
    }
    
    int top() {
        return q1.front();
    }
    
    bool empty() {
        return q1.empty();
    }
};
```

Approach 2 : one queue
```
class MyStack {
queue <int> q;
public:
    MyStack() {
        
    }
    
    void push(int x) {
        q.push(x);
        int cnt = 0;
        while(cnt != q.size() - 1){
            int top = q.front();
            q.pop();
            q.push(top);
            cnt++;
        }
    }
    
    int pop() {
        int top = q.front();
        q.pop();
        return top;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};
