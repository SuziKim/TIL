## 2D Array - DS (HackerRank)

<https://www.hackerrank.com/challenges/2d-array>

---
```C++
// Complete the hourglassSum function below.
int hourglassSum(vector<vector<int>> arr) {
    if (arr.size() <= 2) 
        return 0;

    int max_glass_sum = -64;
    for (int i = 1; i < arr.size() - 1; ++i) {
        for (int j = 1; j < arr.size() - 1; ++j) {
            int glass_sum = arr[i-1][j-1] + arr[i-1][j] + arr[i-1][j+1];
            glass_sum += arr[i][j];
            glass_sum += arr[i+1][j-1] + arr[i+1][j] + arr[i+1][j+1];

            max_glass_sum = max(max_glass_sum, glass_sum);
        }
    }

    return max_glass_sum;
}
```
