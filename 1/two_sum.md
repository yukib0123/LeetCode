```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> num_to_index; // element to index
        for (int i = 0; i < nums.size(); i++) {
            auto itr = num_to_index.find(target - nums[i]);
            if (itr != num_to_index.end()) return {itr->second, i};
            num_to_index[nums[i]] = i;
        }
        // ここには本来到達しません
        return {};
    }
};
```
