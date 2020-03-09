### Balanced Brackets

<https://www.hackerrank.com/challenges/balanced-brackets>

```C++
bool isPair(char left, char right) {
    switch (left) {
        case '[':
        return (right == ']') ? true : false;

        case '{':
        return (right == '}') ? true : false;

        case '(':
        return (right == ')') ? true : false;

        default:
        return false;
    }
}

bool isLeft(char item) {
    switch (item) {
        case '[':
        case '{':
        case '(':
        return true;
    }

    return false;
}

string isBalanced(string s) {
    stack<char> lefts;
    for (char& c: s) {
        if (isLeft(c)) {
            lefts.push(c);
        } else {
            if (lefts.empty()) {
                return "NO";
            }

            char left = lefts.top();
            lefts.pop();
            if (!isPair(left, c)) {
                return "NO";
            }
        }
    }

    return (lefts.empty()) ? "YES" : "NO";
}
```
