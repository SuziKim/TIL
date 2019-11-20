## Rotate Image (LeetCode)

<https://leetcode.com/problems/rotate-image/>

---
### Observation

 - 4개 숫자 내부에서 cyclic rotated된다

### Solution

```C++
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int size = matrix[0].size();
        int n = size - 1;
        for (int i = 0; i < (size + 1) / 2; ++i) {
            for (int j = 0; j < size / 2; ++j) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[n-j][i];
                matrix[n-j][i] = matrix[n-i][n-j];
                matrix[n-i][n-j] = matrix[j][n-i];
                matrix[j][n-i] = temp;
            }
        }
    }
};
```
