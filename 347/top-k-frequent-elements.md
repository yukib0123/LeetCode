```C++
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        map<int, int> freq; // element to frequency
        for (int num : nums) freq[num]++;
        // frequencyで降順ソートするため，freqの成分を入れ替えた配列を用意
        vector<pair<int, int>> vf; // 要素は(frequency, element)
        for (auto &[element, frequency] : freq) vf.emplace_back(frequency, element);
        sort(vf.rbegin(), vf.rend());
        vector<int> ans(k);
        for (int i = 0; i < k; i++) ans[i] = vf[i].second;
        return ans;
    }
};
```
