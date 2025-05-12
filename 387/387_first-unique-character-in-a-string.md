```C++
class Solution {
public:
    int firstUniqChar(string s) {
        map<char, int> char_to_times;
        for (char c : s) char_to_times[c]++;
        int ans = -1;
        for (int i = 0; i < s.size(); i++) {
            if (char_to_times[s[i]] == 1) {
                ans = i;
                break;
            }
        }
        return ans;
    }
};
```
