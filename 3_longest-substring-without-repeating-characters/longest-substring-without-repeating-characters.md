```C++
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int l = 0, min_length = INT_MAX, sum = 0;
        for (int r = 0; r < nums.size(); r++) {
            sum += nums[r];
            while (sum >= target) {
                min_length = min(min_length, r - l + 1);
                if (min_length == 1) return 1;
                sum -= nums[l++];
            }
        }
        return min_length == INT_MAX ? 0 : min_length;
    }
};
```
