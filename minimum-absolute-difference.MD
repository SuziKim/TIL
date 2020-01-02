## Minimum Absolute Difference in an Array (HackerRank)

<https://www.hackerrank.com/challenges/minimum-absolute-difference-in-an-array>

---
```C++
// Complete the minimumAbsoluteDifference function below.
int minimumAbsoluteDifference(vector<int> arr) {
    std::sort(arr.begin(), arr.end());

    int min_diff = static_cast<int>(1e11);
    for (int i = 1; i < arr.size(); ++i) {
        int curr_diff = fabs(arr[i] - arr[i-1]);
        if (curr_diff < min_diff) {
            min_diff = curr_diff;
        }
    }

    return min_diff;
}
```
