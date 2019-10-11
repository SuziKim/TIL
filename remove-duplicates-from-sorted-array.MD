## Remove Duplicates from Sorted Array @ LeetCode

<https://leetcode.com/problems/remove-duplicates-from-sorted-array>

### Observation

 - Memory usage needs to be `O(1)`
 - Every elements appears earlier than it did in the given array. (new index < old index) 

---
### 1st Approach

```C++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() == 0) {
            return 0;
        }
        
        int i = 0, j = 0;
        while(j < nums.size()) {
            if (nums[i] != nums[j]) {
                nums[++i] = nums[j];
            }
            ++j;
        }
        return ++i;
    }
};
```

