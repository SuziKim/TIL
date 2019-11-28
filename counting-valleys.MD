## Counting Valleys (HackerRank)

<https://www.hackerrank.com/challenges/counting-valleys>

---
```C++
// Complete the countingValleys function below.
int countingValleys(int n, string s) {
    int valley_counter = 0;
    int current_level = 0;
    for (int i = 0; i < n; ++i) {
        if (s.at(i) == 'U') {
            if (current_level == -1) {
                ++valley_counter;
            }
            ++current_level;
        } else if (s.at(i) == 'D') {
            --current_level;
        }
    }
    return valley_counter;
}
```
