```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector <string> res;
        string output = "";
        f(n , res , output , 0 , 0);
        return res;
    }

    void f(int n , vector <string> &res , string output , int l , int r){
        if(output.size() == n * 2){
            res.push_back(output);
            return;
        }

        if(l < n) f(n , res , output + '(' , l + 1 , r);
        if(r < l) f(n , res , output + ')' , l , r + 1);
    }
};
