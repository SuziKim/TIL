## Minimum Swaps 2 (HackerRank)

<https://www.hackerrank.com/challenges/minimum-swaps-2/>

---
```C++
// Complete the minimumSwaps function below.
int minimumSwaps(vector<int> arr) {
    int swap_count = 0;
    for(int i = 0; i < arr.size(); ++i) {
        while(arr[i] != i + 1) {
            int temp = arr[i];
            arr[i] = arr[temp - 1];
            arr[temp - 1] = temp;
            ++swap_count;
        }
    }
    return swap_count;
}
```
