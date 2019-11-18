## Permutations (LeetCode)

<https://leetcode.com/problems/permutations/>

---
### 1st Approach

```C++
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> permutations;
        vector<int> curr;
        
        backtrack(nums, permutations, curr);
        
        return permutations;
    }
    
    void backtrack(const vector<int> &nums, vector<vector<int>> &permutations, vector<int> &curr) {
        if (nums.size() == curr.size()) {
            permutations.push_back(curr);
        } else {
            for (int num: nums) {
                if (find(curr.begin(), curr.end(), num) != curr.end()) {
                    continue;
                }
                
                curr.push_back(num);
                backtrack(nums, permutations, curr);
                curr.pop_back();
            }
        }
    }
};
```

- Keep current generated. 
