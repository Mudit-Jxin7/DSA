![image](https://github.com/Mudit-Jxin7/DSA/assets/97677133/e2d133e4-614d-4e68-8522-9de1a95dd42d)

```
class Solution {
public:
    vector<int> lexicalOrder(int n) {
        vector <int> ans;
        for(int i = 1 ; i <= 9 ; i++){
            f(ans , i , n);     
        }

        return ans;
    }

    void f(vector <int> &ans , int i , int n){
        if(i > n) return ;

        ans.push_back(i);
        for(int j = 0 ; j <= 9 ; j++){
            f(ans , 10 * i + j ,n);
        }
    }
};
