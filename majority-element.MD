## Majority Element @ LeetCode

<https://leetcode.com/problems/majority-element/>.

---
### 1st Approach

```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        std::sort(nums.begin(), nums.end());
        
        int major_threshold = nums.size() / 2;
        int count = 0;
        int prev = -1;
        for (auto &num: nums) {
            if (prev != num) {
                count = 0;
                prev = num;
            }
            ++count;
            if (count > major_threshold) {
                return num;
            }
        }
        
        return prev;
    }
};
```

- 정렬`O(n lg n)`하고 나서 탐색`O(n)`
- 느리다

---
### 2nd Approach

```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        std::unordered_map<int, int> count_map;
        
        for (auto &num: nums) {
            count_map.try_emplace(num, 0);
            ++count_map[num];
        }
        
        int majority = nums.size() / 2;
        for (auto &count: count_map) {
            if (count.second > majority) {
                return count.first;
            }
        }
        
        return std::prev(count_map.end())->second;
    }
};
```
