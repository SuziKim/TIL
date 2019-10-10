## Letter Combinations of a Phone Number @ LeetCode

<https://leetcode.com/problems/letter-combinations-of-a-phone-number>

### Observation

 - 순서가 정해져 있는 조합이므로, `ABCDE == (((AB)C)D)E`.

---
### 1st Approach

```C++
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        vector<string> letters;
        if (digits.size() == 0) {
            return letters;
        }
        
        if (digits.size() == 1) {
            letters = char2str(digit2char(digits.at(0)));
        } else {
            letters = concat(digit2char(digits.at(0)), digit2char(digits.at(1)));
            for (int i = 2; i < digits.size(); ++i) {
                letters = concat(letters, digit2char(digits.at(i)));
            }
        }
        
        return letters;
    }
    
private:
    vector<string> char2str(vector<char> chars) {
        vector<string> strs;
        for (auto c: chars) {
            string str(1, c);
            strs.push_back(str);
        }
        return strs;
    }
    
    vector<string> concat (vector<char> left, vector<char> right) {
        return concat(char2str(left), right);
    }
    
    vector<string> concat (vector<string> left, vector<char> right) {
        vector<string> concatenated;
        
        for (auto &l: left) {
            for (auto &r: right) {
                concatenated.push_back(l + r);
            }
        }
        return concatenated;
    }
    
    vector<char> digit2char(char digit) {
        std::vector<char> chars;
        
        int offset = (digit - '2') * 3;
        if (digit > '7') {
            ++offset;
        }
        
        for (int i = 0; i < 3; ++i) {
            chars.push_back('a' + offset + i);
        }
        
        if (digit == '7') {
            chars.push_back('s');
        }
        if (digit == '9') {
            chars.push_back('z');
        }
        
        return chars;
    }
};
```

