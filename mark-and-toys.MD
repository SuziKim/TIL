## Mark and Toys (HackerRank)

<https://www.hackerrank.com/challenges/mark-and-toys>

---
```C++
// Complete the maximumToys function below.
int maximumToys(vector<int> prices, int k) {
    std::sort(prices.begin(), prices.end());
    int toy_count = 0;
    for(double price: prices) {
        k -= price;
        if (k >= 0) {
            ++toy_count;
        } else {
            break;
        }
    }
    return toy_count;
}
```
