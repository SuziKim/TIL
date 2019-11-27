## Sock Merchant (HackerRank)

<https://www.hackerrank.com/challenges/sock-merchant>

---
```C++
// Complete the sockMerchant function below.
int sockMerchant(int n, vector<int> ar) {
    unordered_map<int, int> socks_counter;
    for (auto &sock: ar) {
        if (socks_counter.find(sock) != socks_counter.end()) {
            socks_counter.at(sock)++;
        } else {
            socks_counter.emplace(sock, 1);
        }
    }

    int count = 0;
    for (auto &socks: socks_counter) {
        count += socks.second / 2;
    }

    return count;
}
```
