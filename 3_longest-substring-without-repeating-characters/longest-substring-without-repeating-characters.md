```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int l = 0;
        int len = s.size();
        int longest_len = 1;
        map<char, int> chara_to_index;
        if (len == 0) return 0;
        for (int r = 0; r < len; r++) {
            if(chara_to_index.find(s[r]) != chara_to_index.end()){ 
                l = max(l, chara_to_index[s[r]] + 1);  
            }          
            chara_to_index[s[r]] = r;
            longest_len = max(longest_len, r - l + 1);
        }
        return longest_len;
    }
};
```
