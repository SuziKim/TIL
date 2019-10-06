## Reverse Integer @ LeetCode

<https://leetcode.com/problems/reverse-integer>

### Observation

 - Palindrome Number <https://github.com/dodam-kim/TIL/blob/master/palindrome-number.MD> 문제와 매우 유사

---
### 1st Approach

```C++
class Solution {
public:
    int reverse(int x) {
        int sign = 1;
        if (x < 0) {
            if (x == INT_MIN) {
                return 0; // Overflow case
            }
            sign = -1;
            x = -x;
        }
        
        int inv_x = 0;
        int overflow_threshold = INT_MAX / 10;
        while (0 < x) {
            if (overflow_threshold < inv_x) {
                return 0; // Overflow case
            }
            inv_x = 10 * inv_x + x % 10;
            x /= 10;
        }
        
        return sign * inv_x;
    }
};
```

- Overflow case에 유의해야 함

