```class Solution {
public:
    bool f(vector <int> &stalls , int mid , int n , int k){
        int c = 1;
        int place = stalls[0];
        
        for(int i = 1 ; i < n ; i++){
            if(stalls[i] - place >= mid){ 
                c++;
                place = stalls[i];
            }
        }
        
        return c >= k;
    }
    
    int solve(int n, int k, vector<int> &stalls) {
        int s = 1 , e = *max_element(stalls.begin() , stalls.end());
        sort(stalls.begin() , stalls.end());
        // cout << endl;
        while(s <= e){
            int mid = (s + e) >> 1;
            if(f(stalls , mid , n , k)){
                // cout << mid << " true " << endl;
                s = mid + 1;
            }else{
                e = mid - 1;
                // cout << mid << " false " << endl;
            }
        }
        
        return e;
        
    }
};
