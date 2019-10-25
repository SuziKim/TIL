## Climbing Stairs @ LeetCode

<https://leetcode.com/problems/climbing-stairs/>

### Observations

- n번째 계단에 도달하는 방법은 1) n-1번째 계단에서 1칸 오르기, 2) n-2번째 계단에서 2칸 오르기로 양분된다.

---
### 1st Approach (Recursive)

```C++
class Solution {
public:
    int climbStairs(int n) {
        if (n <= 1) {
            return 1;
        }
        
        return climbStairs(n - 1) + climbStairs(n - 2);
    }
};
```

- Time Limit Exceed

---
### 2nd Approach (Memoization)

```C++
class Solution {
public:
    int climbStairs(int n) {
        int climbs[n + 1];
        
        climbs[0] = 1;
        climbs[1] = 1;
        
        for (int i = 2; i <= n; ++i) {
            climbs[i] = climbs[i - 1] + climbs[i - 2];
        }
        
        return climbs[n];
    }
};
```

