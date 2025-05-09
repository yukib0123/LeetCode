```C++
class Solution {
public:
    vector<vector<int>> kSmallestPairs(vector<int>& nums1, vector<int>& nums2, int k) {
        using T = tuple<int, int, int>;
        priority_queue<T, vector<T>, greater<T>> pq;
        int n = nums1.size(), m = nums2.size();
        for (int i = 0; i < n && i < k; ++i) pq.emplace(nums1[i] + nums2[0], i, 0);
        vector<vector<int>> ans;
        while (k--) {
            auto [sum, i, j] = pq.top();
            ans.push_back({nums1[i], nums2[j]});
            pq.pop();
            if(j + 1 < m) pq.emplace(nums1[i] + nums2[j+1], i, j+1);
        }
        return ans;    
    }
};
```
