![ReverseString](https://github.com/Mudit-Jxin7/DSA/assets/97677133/2c330cfe-980a-4656-8be2-91c8a84d5f06)

```class Solution {
public:
    string reverseWords(string s) {
        int n = s.size();
        string res = "";
        int i = n - 1, j = n - 1;  // Start from the end of the string

        while (i >= 0) {
            while (i >= 0 && s[i] == ' ') i--;

            j = i;
            while (i >= 0 && s[i] != ' ') {
                i--;
            }

            if (res.empty()) {
                res += s.substr(i + 1, j - i);
            } else {
                res += " " + s.substr(i + 1, j - i);
            }

            while (i >= 0 && s[i] == ' ') i--;
            j = i;

        }

        return res;
    }
};
