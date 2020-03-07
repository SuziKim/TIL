## Alternating Characters (HackerRank)

<https://www.hackerrank.com/challenges/alternating-characters>

```C++
int alternatingCharacters(string s) {
    int remove_count = 0;
    char prev = 0;
    
    for (char& digit: s) {
        if (digit == prev) {
            ++remove_count;
        }
        prev = digit;
    }

    return remove_count;
}
```
