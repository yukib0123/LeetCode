```C++
class Solution {
public:
    std::vector<std::vector<int>> permute(std::vector<int>& nums) {
        backtrack(nums, 0, nums.size()); 
        return result;
    }

private:
    vector<vector<int>> result;
    void backtrack(std::vector<int>& nums, size_t i, size_t n) {
        if (i == n) {
            result.push_back(nums);
            return;
        }
        for (size_t j = i; j < n; ++j) {     
            swap(nums[i], nums[j]);
            backtrack(nums, i + 1, n);
            swap(nums[i], nums[j]);     
        }
    }
};
```
