## Luck Balance (HackerRank)

<https://www.hackerrank.com/challenges/luck-balance>

---
```C++
// Complete the luckBalance function below.
int luckBalance(int k, vector<vector<int>> contests) {
    priority_queue<int> luck_queue;
    int luck = 0;

    for (auto contest: contests) {
        if (contest[1] == 0) {
            luck += contest[0];
        } else {
            luck_queue.push(contest[0]);
        }
    }

    while(!luck_queue.empty()) {
        if (k > 0) {
            luck += luck_queue.top();
        } else {
            luck -= luck_queue.top();
        }
        luck_queue.pop();
        --k;
    }
    return luck;
}
```
