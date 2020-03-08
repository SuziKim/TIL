### Sherlock and the Valid String

<https://www.hackerrank.com/challenges/sherlock-and-valid-string>

```C++
string isValid(string s) {
    int num_letter = 'z' - 'a' + 1;
    vector<int> letter_counter(num_letter, 0);

    for (char& letter: s) {
        ++letter_counter[letter - 'a'];
    }

    unordered_map<int, int> count_hash;
    for (int& count: letter_counter) {
        if (0 < count) {
            if (count_hash.find(count) != count_hash.end()) {
                count_hash.emplace(count, 0);
            }
            ++count_hash[count];
        }
    }

    if (count_hash.empty()) {
        return "YES";
    }

    if (count_hash.size() == 1) {
        return "YES";
        // return (count_hash.begin()->first == 1) ? "YES" : "NO";
    }

    if (count_hash.size() == 2) {
        auto front = count_hash.begin();
        auto back = std::next(front);

        if (front->first == 1 && front->second == 1) {
            return "YES";
        }

        if (back->first == 1 && back->second == 1) {
            return "YES";
        }

        if (front->second == 1) {
            return (front->first == back->first + 1) ? "YES" : "NO";
        }

        if (back->second == 1) {
            return (back->first == front->first + 1) ? "YES" : "NO";
        }
    }

    return "NO";
}
```
