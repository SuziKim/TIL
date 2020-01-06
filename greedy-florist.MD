## Greedy Florist (HackerRank)

<https://www.hackerrank.com/challenges/greedy-florist>

---
```C++
// Complete the getMinimumCost function below.
int getMinimumCost(int k, vector<int> c) {
    std::sort(c.begin(), c.end());
    std::reverse(c.begin(), c.end());
    
    int price_sum = 0;
    for (int i = 0; i < c.size(); ++i) {
        price_sum += c[i] * (i / k + 1);
    }
    return price_sum;
}
```
