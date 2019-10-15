## Single Number @ LeetCode

<https://leetcode.com/problems/single-number/>

---
### 1st Approach

```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        if (nums.size() == 1) {
            return nums[0];
        }
        
        std::sort(nums.begin(), nums.end());
        
        for (int i = 1; i < nums.size() - 1; ++i) {
            if (nums[i] != nums[i-1] && nums[i] != nums[i + 1]) {
                return nums[i];
            }
        }
        
        if (nums[0] != nums[1]) {
            return nums[0];
        }
        
        return nums.back();
    }
};
```

- Time Complexity: `O(n lg n)`

---
### 2nd Approach

```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int a = 0x00;
        
        for(int &num: nums) {
            a ^= num;
        }
        
        return a;
    }
};
```
```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int a = 0x00;
        
        for(int &num: nums)
            a ^= num;
        
        return a;
    }
};
```

- XOR 연산을 이용함. `a XOR a = 0`
- `for`문에 괄호를 없앴을 때 속도가 향상됨
