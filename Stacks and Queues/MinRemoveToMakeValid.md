```
class Solution {
public:
    string minRemoveToMakeValid(string s) {
        int n = s.size();
        stack<int> st;
        vector<bool> remove(n, false);
        int open = 0;

        for (int i = 0; i < n; i++) {
            if (s[i] == '(') {
                st.push(i);
                open++;
            } else if (s[i] == ')') {
                if (open > 0) {
                    st.pop();
                    open--;
                } else {
                    remove[i] = true;
                }
            }
        }

        while (!st.empty()) {
            remove[st.top()] = true;
            st.pop();
        }

        string res;
        for (int i = 0; i < n; i++) {
            if (!remove[i])
                res.push_back(s[i]);
        }

        return res;
    }
};
```
https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/
