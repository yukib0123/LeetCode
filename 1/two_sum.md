```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> index_map; // element to index
        for(int i = 0; i < nums.size(); i++) {
            auto itr = index_map.find(target - nums[i]);
            if (itr != index_map.end()) return {itr->second, i};
            index_map[nums[i]] = i;
        }
        return {};
    }
};
```
