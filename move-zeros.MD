## Move Zeros @ LeetCode

<https://leetcode.com/problems/move-zeroes>

---
### 1st Approach

```C++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int fast = 0, slow = 0;
        
        while (fast < nums.size()) {
            if (nums[fast] != 0) {
                nums[slow++] = nums[fast];
            }
            ++fast;
        }
        
        while (slow < nums.size()) {
            nums[slow] = 0;
            ++slow;
        }
    }
};
```
