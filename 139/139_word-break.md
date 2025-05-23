```C++
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        vector<uint8_t> ok(s.size() + 1, false); //j文字目までの文字を分解できるか(j=0は空文字)
        ok[0] = true;
        for (int i = 1; i <= s.size(); i++) {
            for (int j = 0; j < i; j++) {
                if(find(wordDict.begin(), wordDict.end(), s.substr(j, i - j)) != wordDict.end() && ok[j]) 
                    ok[i] = true;
            }
        }
        return ok.back();
    }
};
```
