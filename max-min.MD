## Max Min (HackerRank)

<https://www.hackerrank.com/challenges/angry-children>

---
```C++
// Complete the maxMin function below.
int maxMin(int k, vector<int> arr) {
    int min = INT_MAX;
    sort(arr.begin(), arr.end());

    cout << k << endl;
    for (int i = k - 1; i < arr.size(); ++i) {
        int temp = arr[i] - arr[i - k + 1];
        if (temp < min) {
            min = temp;
        }
    }
    return min;
}
```
