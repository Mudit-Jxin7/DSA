```
class MinStack {
stack <long long> st;
long long mini;
public:
    MinStack() {
        mini = 1e9;
    }
    
    void push(int val) {
        long long value = val;
        if(st.empty()){
            st.push(value);
            mini = value;
            return;
        }

        if(value < mini){
            st.push(2*value - mini);
            mini = value;
            return;
        }

        st.push(value);

    }
    
    void pop() {
        if(st.top() < mini){
            mini = 2*mini - st.top();
            st.pop();
            return;
        }

        st.pop();
    }
    
    int top() {
        if(st.top() < mini){
            return mini;
        }

        return st.top();
    }
    
    int getMin() {
        return mini;
    }
};
