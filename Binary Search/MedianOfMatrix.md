```class Solution{   
public:
    int f(vector <int> arr , int mid){
        int low = 0 , high = arr.size() - 1;
        while(low <= high){
            int md = (low + high) >> 1;
            if(arr[md] <= mid) low = mid + 1;
            else high = mid - 1;
        }
        return low;
    }
    
    int median(vector<vector<int>> &matrix, int R, int C){
        int low = 1 , high = 1e9 , n = matrix.size() , m = matrixm[0].size;
        while(low <= high){
            int mid = (low + high) >> 1;
            int cnt = 0;
            for(int i = 0 ; i < n ; i++){
                cnt += f(matrix[i] , mid);
            }
            if(cnt <= ( n * m ) / 2) low = mid + 1;
            else high = mid - 1;
        }
        return low;
    }
};
```

Another variant : https://practice.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article
