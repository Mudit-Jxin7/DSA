![Screenshot 2023-05-24 190030](https://github.com/Mudit-Jxin7/DSA/assets/97677133/ad3b0d94-c518-43e1-87b3-c2d2baa9d340)

```
class Solution {
public:
    void f(int ind , int target , vector<int>& candidates , vector<vector<int>> &ans , vector<int> ds){
        if(target == 0){
            ans.push_back(ds);
            return;
        }

        for(int i = ind ; i < candidates.size() ; i++){
            if(i > ind && candidates[i] == candidates[i-1]) continue;

            if(candidates[i] > target) break;

            ds.push_back(candidates[i]);
            f(i + 1 , target - candidates[i] , candidates , ans , ds);
            ds.pop_back();
        }
    }

    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin() , candidates.end());
        vector<vector<int>> ans;
        vector <int> ds;
        f(0 , target , candidates , ans , ds);
        return ans;
    }
};
```


Similar Question : https://leetcode.com/problems/subsets-ii/description/
