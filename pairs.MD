### Pairs (HackerRank)

<https://www.hackerrank.com/challenges/pairs>

```C++
// Complete the pairs function below.
bool contains(const vector<int>& arr, int target, int left, int right) {
    if (right < left) {
        return false;
    }

    int med = (left + right) / 2;
    if (target == arr[med]) {
        return true;
    } else if (target < arr[med]) {
        return contains(arr, target, left, med - 1);
    } else {
        return contains(arr, target, med + 1, right);
    }
}

int pairs(int k, vector<int> arr) {
    if (k == 0) {
        return 0;
    }
    
    std::sort(arr.begin(), arr.end());

    int pair_num = 0;
    for(int left: arr) {
        int target = left + k;
        pair_num += (contains(arr, target, 0, arr.size() - 1)) ? 1 : 0;
    }

    return pair_num;
}
```
