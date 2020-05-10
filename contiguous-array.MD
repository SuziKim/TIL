### Contiguous Array

---
<https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3298/>

```C++
class Solution {
public:
    int findMaxLength(vector<int>& nums) {
        if (nums.size() <= 1) {
            return 0;
        }
        
        unordered_map<int, int> diff_hash;
        
        int max_length = 0;
        int counter = 0;
        for (int i = 0; i < nums.size(); ++i) {
            counter += (nums[i] == 0) ? -1 : 1;
            
            if (counter == 0) {
                max_length = max(max_length, i + 1);
            } else {
                diff_hash.try_emplace(counter, i);
                max_length = max(max_length, i - diff_hash[counter]);
            }
        }
        
        return max_length;
    }
};
```
