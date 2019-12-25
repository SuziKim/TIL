## Two Strings (HackerRank)

<https://www.hackerrank.com/challenges/two-strings>

---
```C++
// Complete the twoStrings function below.
string twoStrings(string s1, string s2) {
    set<char> s1_chars;
    for (auto &c: s1) {
        s1_chars.insert(c);
    }
    for (auto &c: s2) {
        if(s1_chars.find(c) != s1_chars.end()) {
            return "YES";
        }
    }
    return "NO";
}
```
