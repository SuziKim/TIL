### Special String

<https://www.hackerrank.com/challenges/special-palindrome-again>

```C++
bool isSpecial(int n, const string& s, int left, int right) {
    if (n <= right) {
        return false;
    }

    if (right == left) {
        return true;
    }

    char digit = s[left];
    while (left < right) {
        if (s[left] != digit) {
            return false;
        }
        ++left;
        if (s[right] != digit) {
            return false;
        }
        --right;
    }
    return true;
}

long substrCount(int n, string s) {
    queue<pair<int, int>> lr_queue;

    for (int i = 0; i < n; ++i) {
        lr_queue.emplace(i, i);
    }

    long count = 0;
    while (!lr_queue.empty()) {
        auto curr = lr_queue.front();
        lr_queue.pop();
        if (isSpecial(n, s, curr.first, curr.second)) {
            ++count;
        }
        if (curr.second < n) {
            lr_queue.emplace(curr.first, curr.second + 1); 
        }
    }
    return count;
}
```
