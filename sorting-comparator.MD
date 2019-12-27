## Sorting: Comparator (HackerRank)

<https://www.hackerrank.com/challenges/ctci-comparator-sorting>

---
```C++
// complete this method
static int comparator(Player a, Player b)  {
    if (a.score > b.score) {
        return 1;
    } else if (a.score < b.score) {
        return -1;
    }

    if (a.name == b.name) {
        return 0;
    }
    if (a.name > b.name) {
        return -1;
    }
    return 1;
}
```

---
```C++
// complete this method
static int comparator(Player a, Player b)  {
    if (a.score == b.score) {
        if (a.name == b.name) {
            return 0;
        }
        return -1 + 2 * (a.name < b.name);
    }

    return -1 + 2 * (a.score > b.score);
}
```
