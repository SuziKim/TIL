## Jumping On The Clouds (HackerRank)

<https://www.hackerrank.com/challenges/jumping-on-the-clouds>

---
```C++
// Complete the jumpingOnClouds function below.
int jumpingOnClouds(vector<int> c) {
    if (c.size() <= 1) { return 0; }

    int cloud_num = c.size();
    vector<int> min_jumps(cloud_num);
    min_jumps[0] = 0;
    if (c[1] == 0) {
        min_jumps[1] = 1;
    } else {
        min_jumps[1] = cloud_num;
    }

    for (int i = 2; i < cloud_num; ++i) {
        if (c[i] == 1) {
            min_jumps[i] = cloud_num;
        } else {
            min_jumps[i] = min(min_jumps[i - 1], min_jumps[i - 2]);
            ++min_jumps[i];
        }
    }
    
    return min_jumps[cloud_num - 1];
}
```
