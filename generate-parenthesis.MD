## Generate Parentheses (LeetCode)

<https://leetcode.com/problems/generate-parentheses/>

---
### 1st Approach

```C++
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> parenthesis_set;
        string current;
        int counter[2] = {n, 0};
        
        backtrack(counter, current, parenthesis_set);
        return parenthesis_set;
    }
    
    void backtrack(int counter[2], string &current, vector<string> &parenthesis_set) {
        if (counter[0] == 0 && counter[1] == 0) {
            parenthesis_set.push_back(current);
            return;
        }
        
        if (counter[0] > 0) {
            current.push_back('(');
            counter[0]--;
            counter[1]++;
            backtrack(counter, current, parenthesis_set);
            current.pop_back();
            counter[0]++;
            counter[1]--;
        }
        
        if (counter[1] > 0) {
            current.push_back(')');
            counter[1]--;
            backtrack(counter, current, parenthesis_set);
            current.pop_back();
            counter[1]++;
        }
    }
};
```

