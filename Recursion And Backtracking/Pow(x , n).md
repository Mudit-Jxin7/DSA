```
class Solution {
public:
    double myPow(double x, int n) {
        if(n >= 0) return f(x , n);
        return 1 / f(x , n);
    }

    double f(double x , int n){
       if(n == 0) return 1;
       if(n == 1) return x;
       double ans = f(x , n/2);

       if(n&1) return ans * ans * x;
       else return ans * ans;
    }
};
