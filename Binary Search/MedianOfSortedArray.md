```class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
      
        int m = nums1.size();
        int n = nums2.size();
    
       if(m > n)  
           return findMedianSortedArrays(nums2, nums1);
        //MAKE SURE Ensuring that binary search happens on minimum size array

        // Note every time make sure we perform operation on , minimum size of array 
    int low=0,high=m;
    int medianPos=((m+n)+1)/2;
    while(low<=high)
    {
        int cut1 = (low+high)/2;
        int cut2 = medianPos - cut1;
        
       /*
         num1 , num2 both are different array  
        on left half 
        */

        //  INT_MIN initialse if during partition there is no one elements
        // CONDITIONAL OPERATOR
        int l1 = (cut1 == 0)? INT_MIN:nums1[cut1-1];
        int l2 = (cut2 == 0)? INT_MIN:nums2[cut2-1];

        /*
         num1 , num2 both are different array  
        on right half 
        */

        int r1 = (cut1 == m)? INT_MAX:nums1[cut1];
        int r2 = (cut2 == n)? INT_MAX:nums2[cut2];
        

        // this goona valid condition 
        if(l1<=r2 && l2<=r1)
        {
            if((m+n)%2 != 0) 
                 // if odd 
                return max(l1,l2);
            else 
                // if even  
                return (max(l1,l2)+min(r1,r2))/2.0;
        }

        //  this should always do in Binary search 
        else if(l1>r2)
        {
            high = cut1-1;
        }
        else
        {
            low = cut1+1;
        }
    }
    return double(0.0);
    }
};

Variation : https://practice.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article
