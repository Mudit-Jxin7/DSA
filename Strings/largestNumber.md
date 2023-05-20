```
bool compare(string a,string b){
    return a+b > b+a; // for cases like 33 and 332
}

class Solution {
public:
    string largestNumber(vector<int>& nums) {
	
        vector<string> container;
		
        for(int i : nums)  container.push_back(to_string(i));
        
        sort(container.begin(),container.end(),compare);
        
        string result;
        
        for(int i=0;i<container.size();i++)  result+=container[i];
        
        return result[0]=='0'? "0" : result; //cases like 000
    }
};
