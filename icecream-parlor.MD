## Hash Tables: Ice Cream Parlor (HackerRank)

<https://www.hackerrank.com/challenges/ctci-ice-cream-parlor>

---
### 1st Approach

```C++
// Complete the whatFlavors function below.
void whatFlavors(vector<int> cost, int money) {
    int i, j;
    for (i = 0; i < cost.size(); ++i) {
        for (j = 1; j < cost.size(); ++j) {
            if (j == i) {
                continue;
            }
            if (cost[i] + cost[j] == money) {
                cout << i + 1 << " " << j + 1 << endl;
                return;
            }
        }
    }
}
```

- Naive Solution, **Time Limit Exceed**

### 2nd Approach

```C++
// Complete the whatFlavors function below.
void whatFlavors(vector<int> cost, int money) {
    unordered_map<int, int> cost_set;
    for (int i = 0; i < cost.size(); ++i) {
        cost_set.emplace(money - cost[i], i);
    }
    for (int i = 0; i < cost.size(); ++i) {
        auto _pair = cost_set.find(cost[i]);
        if (_pair != cost_set.end() && _pair->second != i) {
            int smaller = min(i + 1, _pair->second + 1);
            int bigger = max(i + 1, _pair->second + 1);
            cout << smaller << " " << bigger << endl;
            return;
        }
    }
}
```
