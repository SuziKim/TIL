## New Year Chaos (HackerRank)

<https://www.hackerrank.com/challenges/new-year-chaos>

---
### 1st Approach (failed)

- Tried to count the people who bribed.

```C++
// Complete the minimumBribes function below.
void minimumBribes(vector<int> q) {
    int bribe_count = 0;
    for (int i = 0; i < q.size(); ++i) {
        if (i + 3 < q[i]) {
            std::cout << "Too chaotic" << std::endl;
            return;
        }
        if (q[i] < i + 1) {
            for (int j = 0; j < i; ++j) {
                if (q[i] < q[j]) {
                    ++bribe_count;
                }
            }
        }
    }
    std::cout << bribe_count << std::endl;
}
```
- Wrong condition: `q[i] < i + 1`. Counterexample: `[1 4 3 2 5]`

```C++
// Complete the minimumBribes function below.
void minimumBribes(vector<int> q) {
    int bribe_count = 0;
    for (int i = 0; i < q.size(); ++i) {
        if (i + 3 < q[i]) {
            std::cout << "Too chaotic" << std::endl;
            return;
        }
        for (int j = 0; j < i; ++j) {
            if (q[i] < q[j]) {
                ++bribe_count;
            }
        }
    }
    std::cout << bribe_count << std::endl;
}
```
- Works, but too slow. Time Complexity = `O(n^2)`

---
### 2nd Approach

```C++
// Complete the minimumBribes function below.
void minimumBribes(vector<int> q) {
    int bribe_count = 0;
    for (int i = q.size() - 1; 0 <= i; --i) {
        if (q[i - 1] == i + 1) {
            // A_(i-1) == i
            q[i - 1] = q[i];
            ++bribe_count;
        } else if (q[i - 2] == i + 1) {
            // A_(i-2) == i
            q[i - 2] = q[i - 1];
            q[i - 1] = q[i];
            bribe_count += 2;
        } else if (q[i] != i + 1) {
            std::cout << "Too chaotic" << std::endl;
            return;
        }
    }
    std::cout << bribe_count << std::endl;
}
```
