## Strings: Making Anagrams (HackerRank)

<https://www.hackerrank.com/challenges/ctci-making-anagrams>

```C++
int makeAnagram(string a, string b) {
    int num_alphabet = 'z' - 'a' + 1;
    vector<int> a_counter(num_alphabet, 0);
    vector<int> b_counter(num_alphabet, 0);

    for (char& digit: a) {
        ++a_counter[digit - 'a'];
    }
    for (char& digit: b) {
        ++b_counter[digit - 'a'];
    }

    int remove_count = 0;
    for (int i = 0; i < a_counter.size(); ++i) {
        remove_count += fabs(a_counter[i] - b_counter[i]);
    }
    return remove_count;
}
```
