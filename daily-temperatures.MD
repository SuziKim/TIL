## Daily Temperatures @ LeetCode

<https://leetcode.com/problems/daily-temperatures/>

---
### 1st Approach

```C++
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) {
        vector<int> days_to_wait(T.size());
        
        days_to_wait.back() = 0;
        for (int i = T.size() - 2; 0 <= i; --i) {
            days_to_wait[i] = 0;
            int j = i + 1;
            
            while (j < T.size()) {
                if (T[i] < T[j]) {
                    days_to_wait[i] = j - i;
                    break;
                }
                if (days_to_wait[j] == 0) {
                    break;
                }
                j += days_to_wait[j];
            }
        }
        
        return days_to_wait;
    }
};
```
