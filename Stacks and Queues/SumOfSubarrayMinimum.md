```
class Solution {
public:
    int sumSubarrayMins(vector<int>& arr) {
        long long n = arr.size();
        stack<pair<long long, long long>> st1;
        stack<pair<long long, long long>> st2;

        vector<long long> left(n);
        vector<long long> right(n);

        for (long long i = 0; i < n; i++) {
            long long curr = arr[i];
            long long cnt = 1;
            while (!st1.empty() && st1.top().first >= curr) {
                cnt += st1.top().second;
                st1.pop();
            }
            st1.push({curr, cnt});
            left[i] = cnt;
        }

        for (long long i = n - 1; i >= 0; i--) {
            long long curr = arr[i];
            long long cnt = 1;
            while (!st2.empty() && st2.top().first > curr) {
                cnt += st2.top().second;
                st2.pop();
            }
            st2.push({curr, cnt});
            right[i] = cnt;
        }

        long long sum = 0;
         int mod = 1e9 + 7;
        for (int i = 0; i < n; i++) {
            sum = (sum + arr[i] * left[i] * right[i]) % mod;
        }
        return sum;
    }
};
```
Similar Question : https://leetcode.com/problems/sum-of-subarray-ranges/description/
