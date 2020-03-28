### Fizz Buzz (LeetCode)

<https://leetcode.com/problems/fizz-buzz/>

```C++
class Solution {
public:
    vector<string> fizzBuzz(int n) {
        vector<string> fizz_buzz;
        for (int i = 1; i <= n; ++i) {
            string item = "";
            if (i % 3 == 0) {
                item += "Fizz";
            }
            if (i % 5 == 0) {
                item += "Buzz";
            }
            if (item.empty()) {
                item += to_string(i);
            }
            fizz_buzz.push_back(item);
        }
        
        return fizz_buzz;
    }
};
```
