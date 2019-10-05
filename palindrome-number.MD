## Palindrome Number @ LeetCode

<https://leetcode.com/problems/palindrome-number>

---
### 1st Approach

```C++
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        
        std::string str_x = "";
        while (x > 0) {
            str_x += '0' + (x % 10);
            x /= 10;
        }
        
        int len = str_x.size();
        for (int head = 0, tail = len-1; head < tail; ++head, --tail) {
            if (str_x.at(head) != str_x.at(tail)) {
                return false;
            }
        }
        
        return true;
    }
};
```

- 처음에 `str_x` 대신 `int inv_x;`로 구현했는데 `inv_x > MAX_INT`인 케이스를 처리하지 못함

---
### 2nd Approach: Implementation of Solution

```C++
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        if (x % 10 == 0 && x != 0) {
            return false;
        }
        
        int inv_x = 0;
        
        while(inv_x < x) {
            inv_x = inv_x * 10 + x % 10;
            x /= 10;
        }
        
        return inv_x == x || inv_x / 10 == x;
    }
};
```

- Based on the fact; Palindrome의 앞쪽 절반과 뒤쪽 절반이 같으므로 반만큼만 처리하면 됨
