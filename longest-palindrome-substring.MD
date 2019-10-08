## Longest Palindrome Substring @ LeetCode

<https://leetcode.com/problems/longest-palindromic-substring>

### 1st Approach

```C++
class Solution {
public:
    string longestPalindrome(string s) {
        if (s.size() <= 1) { 
            return s;
        }
        
        int start = 0, end = 0;
        for (int i = 0; i < s.size(); ++i) {
            int len1 = expandPalindrome(s, i, i);
            int len2 = expandPalindrome(s, i, i+1);
            int len = std::max(len1, len2);
            if (len > end - start + 1) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        
        return s.substr(start, end - start + 1);
    }

private:
    int expandPalindrome(string s, int left, int right) {
        while (0 <= left && right < s.size() && s.at(left) == s.at(right)) {
            left--;
            right++;
        }
        
        return right - left - 1;
    }
};
```
- Really tricky
- `substr()`

