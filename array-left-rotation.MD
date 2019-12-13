## Arrays Left Rotation (HackerRank)

<https://www.hackerrank.com/challenges/ctci-array-left-rotationy>

---
```C++
// Complete the rotLeft function below.
vector<int> rotLeft(vector<int> a, int d) {
    d = d % a.size();
    for (int i = 0; i < d; ++i) {
        a.push_back(a.front());
        a.erase(a.begin());
    }
    return a;
}
```
