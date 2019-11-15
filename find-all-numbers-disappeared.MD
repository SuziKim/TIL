## Find All Numbers Disappeared in an Array (LeetCode)

<https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/>

---

```C++
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int> disappeared;
        
        for (int i = 0; i < nums.size(); ++i) {
            int val = std::fabs(nums[i]) - 1;
            if (nums[val] > 0) {
                nums[val] = -nums[val];
            }
        }
        
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[i] > 0) {
                disappeared.push_back(i + 1);
            }
        }
        
        return disappeared;
    }
};
```

- Mark appearance by sign.
