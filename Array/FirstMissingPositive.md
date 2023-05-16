![firstmissingpositive](https://github.com/Mudit-Jxin7/DSA/assets/97677133/6217b951-2d35-4e1c-9002-1bae10663411)


```class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();
        for(int i = 0 ; i < n ; i++){
            long long element = nums[i];
            long long position = element - 1;
            if(element > 0 && element <= n && nums[position] != element){
                swap(nums[i] , nums[position]);
                i--;
            }
        }

        for(int i = 0 ; i < n ; i++){
            if(nums[i] != i + 1) return i + 1;
        }

        return n + 1;
    }
};
