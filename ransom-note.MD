## Hash Tables: Ransom Note (HackerRank)

<https://www.hackerrank.com/challenges/ctci-ransom-note>

---
```C++
// Complete the checkMagazine function below.
void checkMagazine(vector<string> magazine, vector<string> note) {
    multiset<string> mag_set;
    for (auto &word: magazine) {
        mag_set.insert(word);
    }

    for (auto &word: note) {
        auto curr = mag_set.find(word);
        if (curr != mag_set.end()) {
            mag_set.erase(curr);
        } else {
            cout << "No" << endl;
            return;
        }
    }

    cout << "Yes" << endl;
}
```

---
```C++
// Complete the checkMagazine function below.
void checkMagazine(vector<string> magazine, vector<string> note) {
    multiset<string> note_set;
    for (auto &word: note) {
        note_set.insert(word);
    }

    for (auto &word: magazine) {
        auto curr = note_set.find(word);
        if (curr != note_set.end()) {
            note_set.erase(curr);
        }

        if (note_set.empty()) {
            cout << "Yes" << endl;
            return;
        }
    }

    cout << "No" << endl;
}
```
