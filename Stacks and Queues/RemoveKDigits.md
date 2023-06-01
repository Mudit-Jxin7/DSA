```
class Solution {
public:
    string removeLeadingZeros(string& str) {
    size_t pos = str.find_first_not_of('0');  // Find first non-zero digit position
    
    if (pos == std::string::npos) {
        // If all characters are zeros, return a string with a single zero
        return "0";
    }
    
    // Return the substring starting from the first non-zero digit
    return str.substr(pos);
}

    string removeKdigits(string num, int k) {
        stack <char> st;
        int n = num.size();
        for(int i = 0 ; i < n ; i++){
            char ch = num[i];
            while(!st.empty() && st.top() > ch && k > 0){
                st.pop();
                k--;
            }

            st.push(ch);
        }

        while(k > 0){
            st.pop();
            k--;
        }

        string res = "";
        while(st.size() > 0){
            res.push_back(st.top());
            st.pop();
        }
        reverse(res.begin() , res.end());
        if(res == "") return "0";
        string result = removeLeadingZeros(res);
        return result;
    }
};
