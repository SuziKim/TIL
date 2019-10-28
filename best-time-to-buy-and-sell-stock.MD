## Best Time to Buy and Sell Stock @ LeetCode

<https://leetcode.com/problems/best-time-to-buy-and-sell-stock/>

---
### Observations

- Need to keep min_price before current. max_price could be taken immediately.

### 1st Approach

```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min_price = INT_MAX;
        int max_profit = 0;
        
        for (auto &price: prices) {
            if (price < min_price) {
                min_price = price;
            } else if (price - min_price > max_profit) {
                max_profit = price - min_price;
            }
        }
        
        return max_profit;
    }
};
```
