### Plus Minus

---
<https://www.hackerrank.com/challenges/plus-minus/problem>

```C++
// Complete the plusMinus function below.
void plusMinus(vector<int> arr) {
    vector<int> counts = {0, 0, 0};

    for(int value: arr) {
        int index = (value == 0) ? 2 : ((value < 0) ? 1 : 0);
        ++counts[index];
    }

    for(int count: counts) {
        cout << (double)count / arr.size() << endl;
    }
}
```
