```
class Solution {
public:
    int maxScoreWords(vector<string>& words, vector<char>& letters, vector<int>& score) {
        vector <int> freq(26 , 0);
        for(int i = 0 ; i < letters.size() ; i++){
            char ch = letters[i];
            freq[ch - 'a']++;
        }

        return f(words , freq , score , 0);
    }

    int f(vector<string>& words, vector<int>& letters, vector<int>& score , int i){
        if(i == words.size()) return 0;

        //notTake
        int sno = f(words , letters , score , i + 1);

        //Take
        int stake = 0;
        int sword = 0;
        bool flag = true;
        string res = words[i];
        for(int ind = 0 ; ind < res.size() ; ind++){
            char ch = res[ind];
            if(letters[ch - 'a'] == 0){
                flag = false;
            }

            letters[ch - 'a']--;
            sword += score[ch - 'a'];
        }

        if(flag){
            stake = sword + f(words , letters , score , i + 1);
        }

        for(int ind = 0 ; ind < res.size() ; ind++){
            char ch = res[ind];
            letters[ch - 'a']++;
        }

        return max(stake , sno);
    }
};
