```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) { 
        int total_profit = 0, min_price = prices[0];
        for(int i = 0; i < prices.size() - 1; i++) {
            int gain = prices[i + 1] - prices[i];
            if (gain > 0) total_profit += gain;
        }
        return total_profit;
    }
};
```
