```C++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int l = 0;  // 一番左端の0のインデックス
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != 0) {
                swap(nums[i], nums[l]);
                l++;
                // swap(nums[i], nums[l++]); //　同じ処理を1行で
            }
        }
    }
};
```
