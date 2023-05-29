```
vector<long long int> twoOddNum(long long int Arr[], long long int N)  
    {
        //xorr everyone
        int xorr = 0;
        for(int i = 0 ; i < N ; i++){
            xorr ^= Arr[i];
        }
        
        
        //rightmost set bit mask
        
        int rmsb = xorr & -xorr;
        
        
        //seperate two grp of number with rsmb 0 and 1 , xor them to get two numbers
        int xorr1 = 0;
        int xorr2 = 0;
    
        for(int i = 0 ; i < N ; i++){
            if((Arr[i] & rmsb) == 0) xorr1 ^= Arr[i];
            else xorr2 ^= Arr[i];
        }
        
        if(xorr1 > xorr2) return {xorr1 , xorr2};
        
        return {xorr2 , xorr1};
        
        
    }
