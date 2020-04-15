### Counting Elements (LeetCode)

<https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3289/>

```C++
class Solution {
public:
    int countElements(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        
        int count = 0;
        
        int i = 0;
        while (i < arr.size()) {
            int next_i = i;
            for (; next_i < arr.size() && arr[i] == arr[next_i]; ++next_i);
            if (next_i == arr.size()) {
                break;
            }
            if (arr[next_i] - 1 == arr[i]) {
                count += (next_i - i);
            }
            i = next_i;
        }
        
        return count;
    }
};
```
