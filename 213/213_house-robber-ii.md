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

修正版
```C++
class Solution {
public:
    int rob(vector<int>& nums) {
        int n = nums.size();
        if (n == 1) return nums[0];
        return max(robbing(nums, 0, n - 1), robbing(nums, 1, n));
    }
private:
    // 配列numsのインデックス[start, end)から得る最大値を返す
    int robbing(vector<int>& nums, size_t start, size_t end) {
        int pre = 0, cur = 0;
        for(int i = start; i < end; i++) {
            int tmp = cur;
            cur = max(cur, pre + nums[i]);
            pre = tmp;
        }
        return cur;
    }
};
```

