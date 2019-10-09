## Valid Parentheses @ LeetCode

<https://leetcode.com/problems/valid-parentheses>

### Observation

- Common stack-using problem

### 1st Approach

```C++
class Solution {
public:
    bool isValid(string s) {
        std::stack<char> bracket_stack;
        for (char &c: s) {
            if (c == '(' || c == '{' || c == '[') {
                bracket_stack.push(c);
            } else {
                if (bracket_stack.size() == 0) {
                    return false;
                }
                if (!isCoupled(bracket_stack.top(), c)) {
                    return false;
                }
                bracket_stack.pop();
            }
        }
        
        return bracket_stack.size() == 0;
    }
    
private:
    bool isCoupled(char open, char close) {
        if (open == '(' && close == ')') {
            return true;
        }
        if (open == '{' && close == '}') {
            return true;
        }
        if (open == '[' && close == ']') {
            return true;
        }
        
        return false;
    }
};
```
- Usage of `std::stack`: `pop()` has NO return.
