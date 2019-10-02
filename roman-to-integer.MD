## Roman to Integer @ LeetCode

<https://leetcode.com/problems/roman-to-integer>

### Observation

 - 각 문자가 나타내는 숫자의 총합이 정답
 - IV, IX, XL...등 특정 두 개의 문자가 연속해서 나타났을 때 문자가 나타내는 수를 빼는 경우: 두 개의 문자가 increasing order로 정렬

---
### 1st Approach

```C++
class Solution {
public:
    std::unordered_map<char, int> makeLookup() {
        std::unordered_map<char, int> roman2int;
        roman2int.emplace('I', 1);
        roman2int.emplace('V', 5);
        roman2int.emplace('X', 10);
        roman2int.emplace('L', 50);
        roman2int.emplace('C', 100);
        roman2int.emplace('D', 500);
        roman2int.emplace('M', 1000);
        
        return roman2int;
    }
    
    int romanToInt(string s) {
        auto roman2int = makeLookup();
        
        int prev = 0;
        int curr = 0;
        
        int sum = 0;
        for (auto &c: s) {
            prev = curr;
            curr = roman2int[c];
            if (prev < curr) {
                sum -= (2 * prev);
            }
            
            sum += curr;
        }
        
        return sum;
    }
};
```

- Nested condition이 가독성이 떨어지는 것 같아서 hashmap으로 만들었으나 수행시간이 길어짐

---
### 2nd Approach

```C++
class Solution {
public:
    int roman2int(char roman) {
        switch(roman) {
            case 'I':
                return 1;
            case 'V':
                return 5;
            case 'X':
                return 10;
            case 'L':
                return 50;
            case 'C':
                return 100;
            case 'D':
                return 500;
            case 'M':
                return 1000;
            default:
                return 0;
        }
    }
    
    int romanToInt(string s) {
        int prev = 0;
        int curr = 0;
        
        int sum = 0;
        for (auto &c: s) {
            prev = curr;
            curr = roman2int(c);
            if (prev < curr) {
                sum -= (2 * prev);
            }
            
            sum += curr;
        }
        
        return sum;
    }
};
```

- Straightforware implementation on observation. 매우 빠르다.

---
### 3rd Approach

`emplace`를 `insert`로 바꿔봄. 약간의 속도 향상
