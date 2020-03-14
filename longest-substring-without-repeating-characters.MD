### Longest Substring Without Repeating Characters

<https://leetcode.com/problems/longest-substring-without-repeating-characters/>

```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if (s.size() == 0) {
            return 0;
        }
        
        unordered_map<char, int> idx_dict;
        
        int num_char = 'z' - 'a' + 1;
        vector<int> substring(s.size(), 0);
        
        substring[0] = 1;
        idx_dict[s[0]] = 0;
        int max_length = 1;
        
        for (int i = 1; i < s.size(); ++i) {
            if (idx_dict.find(s[i]) != idx_dict.end()) {
                substring[i] = std::min(substring[i - 1] + 1, i - idx_dict[s[i]]);
            } else {
                substring[i] = substring[i - 1] + 1;
            }
            idx_dict[s[i]] = i;
            max_length = std::max(substring[i], max_length); 
        }
        
        return max_length;
    }
};
```
