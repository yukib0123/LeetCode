```C++
class Solution {
public:
    int rob(vector<int>& nums) {
        int n = nums.size();
        if (n == 1) return nums[0];
        vector<int> money_sum(n, 0);
        // when rob nums[0]
        money_sum[0] = nums[0];
        money_sum[1] = nums[0];
        for (int i = 2; i < n - 1; i++) {
            money_sum[i] = max(money_sum[i - 2] + nums[i], money_sum[i - 1]);
        }
        int ans = money_sum[n - 2];
        money_sum.assign(n, 0);
        // when not rub nums[0]
        money_sum[1] = nums[1];
        for (int i = 2; i < n; i++) {
            money_sum[i] = max(money_sum[i - 2] + nums[i], money_sum[i-1]);
        }
        return max(ans, money_sum[n - 1]);
    }
};
```
