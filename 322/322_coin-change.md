whileループで重複のある無駄な更新をしている
O(amount^2 * #coins)
```C++
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int inf = 1 << 30;
        vector<int> num_coins(amount + 1, inf);
        num_coins[0] = 0;
        for (int i = 1; i <= amount; i++) {
            for(int x : coins) {
                int j = i - x;
                int cnt = 0;
                while( j >= 0){
                    cnt++;
                    num_coins[i] = min(num_coins[i], num_coins[j] + cnt);
                    j -= x;
                }
            }
        }
        return num_coins[amount] == inf ? -1 : num_coins[amount];
    }
};
```

改善例
O(amount * #coins)
```C++
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int inf = 1 << 30;
        vector<int> num_coins(amount + 1, inf);
        num_coins[0] = 0;
        for (int cur = 1; cur <= amount; cur++) {
            for(int value : coins) {
                if (cur - value >= 0) num_coins[cur] = min(num_coins[cur], num_coins[cur - value] + 1);
            }
        }
        return num_coins[amount] == inf ? -1 : num_coins[amount];
    }
};
```
