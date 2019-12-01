## Repeated String (HackerRank)

<https://www.hackerrank.com/challenges/repeated-string>

---
```C++
// Complete the repeatedString function below.
long repeatedString(string s, long n) {
    int s_size = s.size();
    long dummy = n % s_size;
    long quot = n / s_size;

    int dummy_count = 0;
    int count = 0;
    for (int i = 0; i < s_size; ++i) {
        if (s.at(i) == 'a') {
            if (i < dummy) {
                ++dummy_count;
            }
            ++count;
        }
    }

    return count * quot + dummy_count;
}
```
