## Longest Common Prefix @ LeetCode

<https://leetcode.com/problems/longest-common-prefix>

### 1st Approach

```C++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.size() == 0) {
            return "";
        }
        
        // Get the length of shortest string
        int len = strs[0].size();
        for (auto &str: strs) {
            len = std::min(len, (int)str.size());
        }
        
        std::string prefix;
        for (int i = 0; i < len; ++i) {
            char target = strs[0].at(i);
            for (auto &str: strs) {
                if (str.at(i) != target) {
                    return prefix;
                }
            }
            prefix += target;
        }
        
        return prefix;
    }
};
```
- Naive solution.
- Needs to take account of *empty input*.
