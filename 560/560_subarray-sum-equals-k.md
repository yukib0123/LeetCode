O(n^2)
```C++
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int len = nums.size();
        vector<int> sum(len+1, 0);
        sum[1] = nums[0];
        for (int i = 1; i < len; i++) sum[i + 1] = sum[i] + nums[i];
        int ans = 0;
        for (int i = 1; i <= len; i++) {
            for (int j = 1; j <= i; j++) {
                if(sum[len - i + j] - sum[j - 1] == k) ans++;
            }
        }
        return ans;
    }
};
```

O(nlogn)
```C++
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        map<int, int> sum_to_freq;
        int sum = 0, ans = 0;
        sum_to_freq[sum] = 1;
        for (int num : nums) {
            sum += num;
            if (sum_to_freq.find(sum - k) != sum_to_freq.end()) ans += sum_to_freq[sum - k];
            sum_to_freq[sum]++;
        }
        return ans;
    }
};
```
