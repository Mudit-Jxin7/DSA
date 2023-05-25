![palindromePartitioning](https://github.com/Mudit-Jxin7/DSA/assets/97677133/ca7279c6-7801-4955-b3ac-2e25b9107c65)

```
class Solution {
public:
    vector<vector<string>> partition(string s) {
        vector<vector<string>> res;
        vector <string> path;
        f(0 , s , path , res);
        return res;
    }

    void f(int index , string s , vector <string> path , vector <vector<string>> &res){
        if(index == s.size()){
            res.push_back(path);
            return;
        }

        for(int i = index ; i < s.size() ; i++){
            if(isPalindrome(s , index , i)){
                path.push_back(s.substr(index , i - index + 1));
                f(i + 1 , s , path , res);
                path.pop_back();
            }
        }
    }

    bool isPalindrome(string s , int start , int end){
        while(start <= end){
            if(s[start++] != s[end--]) return 0;
        }

        return 1;
    }

};
