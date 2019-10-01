## ZigZag Conversion @ LeetCode

<https://leetcode.com/problems/zigzag-conversion>

### Observation

 - 특정 크기의 zigzag unit이 반복되어 나타남
 - Size of each ZigZag unit: `numRows * 2 - 2`
 - 각 row에는 해당 ZigZag unit에서 `row`-th, `-row`-th char가 포함

---
### 1st Approach

```C++
class Solution {
public:
    string convert(string s, int numRows) {
        string converted = "";
        
        int str_len = s.size();
        int zz_len = std::max(numRows, numRows * 2 - 2);
        for (int row = 0; row < numRows; ++row) {
            // offset = row, zz_len - row
            std::vector<int> offsets;
            offsets.push_back(row);
            if (0 < row && row < numRows - 1) {
                offsets.push_back(zz_len - row);
            }
            for (int base = 0; base < str_len; base += zz_len) {
                for (auto &offset: offsets) {
                    if (base + offset < str_len) {
                        converted += s.at(base + offset);
                    }
                }
            }
        }
        
        return converted;
    }
};
```
 - Offset을 매번 계산하지 않기 위해 도입한 vector가 오히려 비효율을 초래함
 
---
### 2nd Approach

```C++
class Solution {
public:
    string convert(string s, int numRows) {
        string converted = "";
        
        int str_len = s.size();
        int zz_len = std::max(numRows, numRows * 2 - 2);
        for (int row = 0; row < numRows; ++row) {
            // offset = row, zz_len - row
            for (int i = 0; i < str_len; i++) {
                int offset = i % zz_len; 
                if (offset == row || offset == (zz_len - row)) {
                    converted += s.at(i);
                }
            }
        }
        
        return converted;
    }
};
```
- Naive solution.

---
### 3rd Approach

```C++
class Solution {
public:
    string convert(string s, int numRows) {
        string converted = "";
        
        int str_len = s.size();
        int zz_len = std::max(numRows, numRows * 2 - 2);
        for (int row = 0; row < numRows; ++row) {
            for (int base = 0; base + row < str_len; base += zz_len) {
                converted += s.at(base + row);
                if (row != 0 && row != numRows - 1) {
                    if ((base + zz_len - row) < str_len) {
                        converted += s.at(base + zz_len - row);
                    } 
                }
            }
        }
        
        return converted;
    }
};
```

- 첫번째 방법의 변형
