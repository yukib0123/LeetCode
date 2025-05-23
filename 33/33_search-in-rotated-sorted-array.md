```C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int min_idx = find_min_index(nums);
        int left, right;
        if (min_idx == 0) {
            left = 0; 
            right = nums.size() - 1;
        }
        else {
            if(nums[0] > target) {
                left = min_idx; 
                right = nums.size() - 1;
            }
            else {
                left = 0; 
                right = min_idx - 1;
            }
        }
        auto itr = lower_bound(nums.begin() + left, nums.begin() + right, target);
        int idx = distance(nums.begin(), itr);
        return nums[idx] == target ? idx : -1;
    }
private:
    int find_min_index(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        if(nums[left] < nums[right]) return 0;
        while (right - left > 1) {
            int middle = left + (right - left) / 2;
            if (nums[middle] < nums[right]) right = middle;
            else left = middle;
        }
        return right;
    }
};
```
