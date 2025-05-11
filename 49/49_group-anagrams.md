```C++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        map<string, vector<string>> anagram_to_words;
        for (string word : strs) {
            string anagram = word;
            sort(anagram.begin(), anagram.end());
            anagram_to_words[anagram].push_back(word); 
        }
        vector<vector<string>> ans;
        for (auto entry : anagram_to_words) {
            ans.push_back(entry.second);
        }
        return ans;
    }
};
```
